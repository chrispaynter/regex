# Regex helpers
## Converting C# models into typescript models

### Example C# class

```c#
public class Advantage
{
    public string AccessCode { get; set; }
    public AdvantageTargetType AdvantageTargetType { get; set; }
    public AdvantageType AdvantageType { get; set; }
    public bool AllowPurchaseCulturalContact { get; set; }
    public bool AutoPromote { get; set; }
    public string Code { get; set; }
    public ContactLimitation ContactLimitation { get; set; }
    public long DiscountAmount { get; set; }
    public long DiscountPaymentMethodId { get; set; }
    public DateTime End { get; set; }
    public long EndRelative { get; set; }
    public bool Exclusive { get; set; }
    public ExternalName ExternalDescription { get; set; }
    public ExternalName ExternalName { get; set; }
    public IEnumerable<long> FreeShipmentModeIds { get; set; }
    public long Id { get; set; }
    public Image Image { get; set; }
    public string LargeImageUrl { get; set; }
    public string Logo { get; set; }
    public bool MandatoryContact { get; set; }
    public long MaxOrderQuantity { get; set; }
    public int MaxQuantityPerPerformance { get; set; }
    public string MediumImageUrl { get; set; }
    public PerformanceEndDateType PerformanceEndDateType { get; set; }
    public IEnumerable<Product> Products { get; set; }
    public bool SingleSeatCatPerPerformance { get; set; }
    public DateTime Start { get; set; }
    public long StartRelative { get; set; }
    public State State { get; set; }
}
```

### Regex

#### Find

```
public ([^"]+) ([\w]{1})([\w]+) ([^"]+)
```

#### Replace

Note the use of `\L` to lower case the first letter of the property name

```
\L$2$3: $1;
```

Example in VS Code below

![image-20220115182836359](/Users/chrispaynter/Development/chrispaynter/regex/images/README/image-20220115182836359.png)

### Result

Not perfect, but gets you 90% the way there.

```
public class Advantage
{
    accessCode: string;
    advantageTargetType: AdvantageTargetType;
    advantageType: AdvantageType;
    allowPurchaseCulturalContact: bool;
    autoPromote: bool;
    code: string;
    contactLimitation: ContactLimitation;
    discountAmount: long;
    discountPaymentMethodId: long;
    end: DateTime;
    endRelative: long;
    exclusive: bool;
    externalDescription: ExternalName;
    externalName: ExternalName;
    freeShipmentModeIds: IEnumerable<long>;
    id: long;
    image: Image;
    largeImageUrl: string;
    logo: string;
    mandatoryContact: bool;
    maxOrderQuantity: long;
    maxQuantityPerPerformance: int;
    mediumImageUrl: string;
    performanceEndDateType: PerformanceEndDateType;
    products: IEnumerable<Product>;
    singleSeatCatPerPerformance: bool;
    start: DateTime;
    startRelative: long;
    state: State;
}
```

