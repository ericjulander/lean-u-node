# City Organizer

You are tasked with converting a csv into a markdown file. Reading in US Census data which contains the population for a 1000 cities, grouping the data by Region and State.

##### Rules
 - **Not allowed to use `for` loops.**
 - **Avoid using the `foreach` method**

In order to get familiar with using Array methods, the only rule is that you are not allowed to use traditional `for` loops. The more you use Array methods like [`.reduce`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce) and [`.filter`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) instead of [`.forEach`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach) the better.

## Utils
You have a couple of utility functions provided for you

#### read( `csvFileName` )
Will read in and parse the given file. Returning something that looks like this
``` js
[{ 
    Region:"Northeast",
    State:"New York",
    City:"New York, NY",
    Population:"8622698",
}, ... ]
```
    
#### write( `markdownFileName` , `regions` )
Creates the markdown file at the specified location, expecting `regions`
to be in a format like this:
``` js
[{
  name: 'Northeast',
  states:[{
    name: 'New York',
    cities:[{
      name: 'New York, NY',
      population: 8622698
    }]
  }]
}]
```

#### prettyprint( `{ Object }` )
To help with debugging, will `console.log`
an object after passing it through [`beautify`](https://www.npmjs.com/package/js-beautify)

## Getting Started

1. Open the terminal
2. Navigate to your Documents folder then run the following to clone the repository
```
git clone https://github.com/byuitechops/city-organizer.git
cd city-organizer
npm i
```
3. Open the created folder in vscode
4. Install the Markdown Preview plugin in vscode to see how your output will be rendered
5. Write some awesome code
5. Run your code by running `node main.js` in the console
6. To run the test cases install jest globaly with
```
npm install -g jest
```

## Challenge #1 Create

**Testing:** run `jest create.test.js`

**Outcome:** Be comfortable with using array methods to manipulate data into different formats

In `main.js` add the nessesary code to transform the flat csv data into the nested format that the `write` function is expecting. If everything goes good the `write` function should create a file that looks like this:
``` md
# Midwest
## Illinois
- Chicago, IL ( `pop. 2,716,450` )

# Mountain
## Arizona
- Phoenix, AZ ( `pop. 1,626,078` )

# Northeast
## New York
- New York, NY ( `pop. 8,622,698` )
## Pennsylvania
- Philadelphia, PA ( `pop. 1,580,863` )

# Pacific
## California
- San Jose, CA ( `pop. 1,035,317` )
- San Diego, CA ( `pop. 1,419,516` )
- Los Angeles, CA ( `pop. 3,999,759` )

# South
## Texas
- Dallas, TX ( `pop. 1,341,075` )
- San Antonio, TX ( `pop. 1,511,946` )
- Houston, TX ( `pop. 2,312,717` )
```

## Challenge #2 Sorting

**Testing:** run `jest sort.test.js`

**Outcome:** Become comfortable with using the `sort` function with multiple different data formats and targets

Complete the following sorting challenges

### Sorting States Alphabetically
Either add code or change your existing code so that states under a REGION are sorted alphabetically
``` md
# Pacific
## California
- Oxnard, CA ( `pop. 210,037` )
## Oregon
- Portland, OR ( `pop. 647,805` )
## Washington
- Tacoma, WA ( `pop. 213,418` )
- Spokane, WA ( `pop. 217,108` )
- Seattle, WA ( `pop. 724,745` )

# Mountain
## Colorado
- Aurora, CO ( `pop. 366,623` )
- Colorado Springs, CO ( `pop. 464,474` )
- Denver, CO ( `pop. 704,621` )
## Idaho
- Boise City, ID ( `pop. 226,570` )
## Nevada
- North Las Vegas, NV ( `pop. 242,975` )
- Reno, NV ( `pop. 248,853` )
- Henderson, NV ( `pop. 302,539` )
- Las Vegas, NV ( `pop. 641,676` )
```

### Sorting Cities by Population
Either add code or change your existing code so that cities under a STATE are sorted by their population
``` md
# Pacific
## California
- Los Angeles, CA ( `pop. 3,999,759` )
- San Diego, CA ( `pop. 1,419,516` )
- San Jose, CA ( `pop. 1,035,317` )
- San Francisco, CA ( `pop. 884,363` )
- Fresno, CA ( `pop. 527,438` )
- Sacramento, CA ( `pop. 501,901` )
- Long Beach, CA ( `pop. 469,450` )
- Oakland, CA ( `pop. 425,195` )
- Bakersfield, CA ( `pop. 380,874` )
- Anaheim, CA ( `pop. 352,497` )
- Santa Ana, CA ( `pop. 334,136` )
- Riverside, CA ( `pop. 327,728` )
- Stockton, CA ( `pop. 310,496` )
- Irvine, CA ( `pop. 277,453` )
- Chula Vista, CA ( `pop. 270,471` )
- Fremont, CA ( `pop. 234,962` )
- San Bernardino, CA ( `pop. 216,995` )
- Modesto, CA ( `pop. 214,221` )
- Fontana, CA ( `pop. 211,815` )
- Santa Clarita, CA ( `pop. 210,888` )
- Oxnard, CA ( `pop. 210,037` )
```

### Sort Regions West to East
Either add code or change your existing code so that the regions are in order of West to East. So they follow as `Pacific, Mountain, Midwest, South, Northeast`,

``` md
# Pacific
## California
- Los Angeles, CA ( `pop. 3,999,759` )
- San Diego, CA ( `pop. 1,419,516` )
- San Jose, CA ( `pop. 1,035,317` )

# Mountain
## Arizona
- Phoenix, AZ ( `pop. 1,626,078` )

# Midwest
## Illinois
- Chicago, IL ( `pop. 2,716,450` )

# South
## Texas
- Houston, TX ( `pop. 2,312,717` )
- San Antonio, TX ( `pop. 1,511,946` )
- Dallas, TX ( `pop. 1,341,075` )

# Northeast
## New York
- New York, NY ( `pop. 8,622,698` )
## Pennsylvania
- Philadelphia, PA ( `pop. 1,580,863` )
```

## Challenge #3 Unique City Names

**Testing:** run `jest unique.test.js`

**Outcome:** Become better at noticing your assumptions

Use the `nonunique.csv` csv instead of `cities.csv`. The only thing that has changed is that city names no longer contain the state name acronym. So there are now 5 cities with the name `Springfield` all in different states. Just making sure that you are not relying on the state names to be unique.

## Challenge #4 Writing

**Testing:** run `jest write.test.js`

**Outcome:** Become more comfortable with researching documentation

Research how to use [fs.writeFileSync](https://nodejs.org/api/fs.html#fs_fs_writefilesync_file_data_options), [fs.readFileSync](https://nodejs.org/api/fs.html#fs_fs_readfilesync_path_options) and [d3.csvParse](https://github.com/d3/d3-dsv#csvParse) to read, write, and parse the CSV. You are not allowed to use the provided `utils` functions in this challenge. You will need to read the csv and write to the file on your own, with the `fs` and `d3-dsv` libraries.

### Output
Using the sorts from the previous challenge. Write out just the first 10 rows to the `output.md` file. That file will be checked that it matches this output exactly.
``` md
# Pacific
## California
- Los Angeles, CA `pop. 3999759`
- San Diego, CA `pop. 1419516`
- San Jose, CA `pop. 1035317`

# Mountain
## Arizona
- Phoenix, AZ `pop. 1626078`

# Midwest
## Illinois
- Chicago, IL `pop. 2716450`

# South
## Texas
- Houston, TX `pop. 2312717`
- San Antonio, TX `pop. 1511946`
- Dallas, TX `pop. 1341075`

# Northeast
## New York
- New York, NY `pop. 8622698`
## Pennsylvania
- Philadelphia, PA `pop. 1580863`
```

## Challenge #5 Summing

**Testing:** run `jest sum.test.js`

**Outcome:** Become better at designing code that has taken into account things that might need to be accessable in the future.

Add the `population` property to Region and States, which contains the sum of the populations beneath them.
``` js
[{
  name: 'Northeast',
  population: 8622698
  states:[{
    name: 'New York',
    population: 8622698
    cities:[{
      name: 'New York, NY',
      population: 8622698
    }]
  }]
}]
```

# Challenge #6 Optimization (just for fun)

**Testing:** run `jest optimize.test.js`

**Outcome:** Become more aware of the costs that come from a specific implementation

Run your code against `all.csv` to see how long it takes. It contains almost 8,500 cities across america. "# lean-u-node" 
