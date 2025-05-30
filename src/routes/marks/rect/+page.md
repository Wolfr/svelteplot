---
title: Rect mark
---

The Rect mark can be used to add rectangles to the plot, defined by x1, y1, x2, and y2 coordinates:

The interval transform may be used to convert a single value in x or y (or both) into an extent. For example, the chart below shows the observed daily maximum temperature in Seattle for the year 2015. The day-in-month and month-in-year numbers are expanded to unit intervals by setting the [interval option](/transforms/interval) to 1.

```svelte live
<script>
    import { Plot, Rect, Text } from 'svelteplot';
    import { page } from '$app/state';
    const { seattle } = $derived(page.data.data);
</script>

<Plot
    aspectRatio={1}
    y={{
        ticks: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11],
        tickFormat: (d) =>
            new Intl.DateTimeFormat('en', {
                month: 'narrow'
            }).format(new Date(2000, d, 1))
    }}
    testid="seattle-temp">
    <Rect
        data={seattle}
        filter={(d) => d.date.getUTCFullYear() === 2015}
        x={(d) => d.date.getUTCDate()}
        y={(d) => d.date.getUTCMonth()}
        interval={1}
        fill="temp_max"
        inset="0.5" />
</Plot>
```

```svelte
<Plot
    aspectRatio={1}
    y={{
        ticks: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11],
        tickFormat: (d) =>
            new Intl.DateTimeFormat('en', {
                month: 'narrow'
            }).format(new Date(2000, d, 1))
    }}>
    <Rect
        data={seattle}
        filter={(d) => d.date.getUTCFullYear() === 2015}
        x={(d) => d.date.getUTCDate()}
        y={(d) => d.date.getUTCMonth()}
        interval={1}
        fill="temp_max"
        inset="0.5" />
</Plot>
```

## RectX

RectX can be used for range annotations:

```svelte live
<script>
    import { Plot, Line, RectX } from 'svelteplot';

    import { page } from '$app/state';
    let { aapl } = $derived(page.data.data);
</script>

<Plot>
    <Line data={aapl} x="Date" y="Close" />
    <RectX
        data={[
            {
                from: new Date(2014, 0, 1),
                to: new Date(2016, 0, 1)
            }
        ]}
        x1="from"
        x2="to"
        fillOpacity={0.1} />
</Plot>
```

```svelte
<Plot>
    <Line data={aapl} x="Date" y="Close" />
    <RectX
        data={[
            {
                from: new Date(2014, 0, 1),
                to: new Date(2016, 0, 1)
            }
        ]}
        x1="from"
        x2="to"
        fillOpacity={0.1} />
</Plot>
```

## RectY

RectY can be used for range annotations:

```svelte live
<script>
    import { Plot, Line, RectY } from 'svelteplot';

    import { page } from '$app/state';
    let { aapl } = $derived(page.data.data);
</script>

<Plot>
    <Line data={aapl} x="Date" y="Close" />
    <RectY
        data={[{ from: 120, to: 140 }]}
        y1="from"
        y2="to"
        fillOpacity={0.1} />
</Plot>
```

```svelte
<Plot>
    <Line data={aapl} x="Date" y="Close" />
    <RectY
        data={[{ from: 120, to: 140 }]}
        y1="from"
        y2="to"
        fillOpacity={0.1} />
</Plot>
```

## Stacking

```svelte live

```
