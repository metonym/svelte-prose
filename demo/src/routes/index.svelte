<script>
  import Prose, { T } from "svelte-prose";
</script>

<svelte:head>
  <title>svelte-prose</title>
</svelte:head>

<Prose>
  <T.H1 text="Articles of Confederation" />
  <p>
    After the first enumeration required by the first article of the
    Constitution, there shall be one Representative for every 30,000 until the
    number shall amount to 100, after which the proportion shall be so regulated
    by Congress, that there shall be not less than 100 Representatives, nor less
    than one Representative for every 40,000 persons, until the number of
    Representatives shall amount to 200; after which the proportion shall be so
    regulated by Congress, that there shall not be less than 200
    Representatives, nor more than one Representative for every 50,000 persons.
  </p>

  <T.H2 text="Article 1" />
  <p>The style of this confederacy shall be "The United States of America."</p>

  <T.H2 text="Article 2" />
  <p>
    Each state retains its sovereignty, freedom, and independence, and every
    power, jurisdiction, and right, which is not by this confederation expressly
    delegated to the United States, in Congress assembled.
  </p>

  <T.H2 text="Article 3" />
  <p>
    The said States hereby severally enter into a firm league of friendship with
    each other, for their common defense, the security of their liberties, and
    their mutual and general welfare, binding themselves to assist each other,
    against all force offered to, or attacks made upon them, or any of them, on
    account of religion, sovereignty, trade, or any other pretense whatever.
  </p>
</Prose>
