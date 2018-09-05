---
title: Numaralandırma türleri (C# programlama Kılavuzu)
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: 3efedd48303c79bafde3704b0fdd6fcdd465a0a7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672237"
---
# <a name="enumeration-types-c-programming-guide"></a>Numaralandırma türleri (C# programlama Kılavuzu)

(Ayrıca bir numaralandırma veya bir sabit listesi adlı) bir numaralandırma türü bir değişkene atanabilir adlandırılmış integral sabitleri tanımlamak için etkili bir yol sağlar. Örneğin, değeri haftanın bir gününü temsil edecek bir değişkeni tanımlamak sahip olduğunuzu varsaymaktadır. Bu değişken her zamankinden depolayacak yalnızca yedi anlamlı değerleri vardır. Bu değerleri tanımlamak için kullanılarak bildirilen bir numaralandırma türü kullanabilirsiniz [enum](../../csharp/language-reference/keywords/enum.md) anahtar sözcüğü.

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

Varsayılan olarak temel alınan her öğenin sabit listesi türünde [int](../../csharp/language-reference/keywords/int.md). Önceki örnekte gösterilen şekilde bir virgül kullanarak başka bir integral sayısal tür belirtebilirsiniz. Olası türlerinin tam listesi için bkz. [enum (C# Başvurusu)](../../csharp/language-reference/keywords/enum.md).

Temel alınan sayısal değerler, aşağıdaki örnekte gösterildiği gibi temel türdeki tür atama doğrulayabilirsiniz.

```csharp
Day today = Day.Monday;
int dayNumber =(int)today;
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);

Month thisMonth = Month.Dec;
byte monthNumber = (byte)thisMonth;
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);

// Output:
// Monday is day number #1.
// Dec is month number #11.
```

Bir sabit listesi yerine bir sayısal tür kullanmanın avantajları şunlardır:

- Açıkça için istemci kodu hangi değişken için geçerli değerler belirtin.

- Visual Studio IntelliSense tanımlanan değerleri listeler.

Numaralandırıcı listesinde öğelerin değerlerini belirtmediğinizde değerleri otomatik olarak 1 artar. Önceki örnekte, `Day.Sunday` 0 değerine sahiptir `Day.Monday` 1 ve benzeri değerine sahiptir. Yeni bir oluşturduğunuzda `Day` nesnesi, varsayılan değerine sahip olacak `Day.Sunday` , açıkça bu değeri atamazsanız (0). Enum oluşturduğunuzda en mantıklı varsayılan değer seçin ve sıfır değerini verin. Oluşturulduğunda kullanıcılara açıkça bir değer atanmaz ise, varsayılan değere sahip tüm sabit listelerini neden.

Değişken `meetingDay` türünde `Day`, sonra da (açık bir yayın olmadan) yalnızca uygulamayı tanımlanan değerlerden birini atayabilirsiniz `Day`. Ve toplantı gün değişirse, yeni bir değer atayabilirsiniz `Day` için `meetingDay`:

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> Rasgele tamsayı değerdeki atamak mümkün mü `meetingDay`. Örneğin, bu kod satırı hata üretmez: `meetingDay = (Day) 42`. Enum değişkeni yalnızca tanımlanan enum değerlerinden biri tutar, örtük beklentisi olduğundan ancak, bunu kullanmayın. Rastgele bir değeri bir sabit listesi türünde bir değişken için bir yüksek riskli hatalara tanıtmak için atamaktır.

Numaralandırıcı listesindeki bir numaralandırma türü öğeler için herhangi bir değer atayın ve hesaplanan değerler de kullanabilirsiniz:

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a>Bit bayrakları olarak numaralandırma türleri

Bir numaralandırma türü bit bayrakları tanımlamak için herhangi bir birleşimini Numaralandırıcı listesinde tanımlanan değerleri depolamak için numaralandırma türünün bir örneği sağlayan kullanabilirsiniz. (Kuşkusuz, bazı birleşimleri anlamlı veya izin verilen program kodunuzda olmayabilir.)

Uygulayarak bir bit bayrakları sabit listesi oluşturma <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği ve değerleri uygun şekilde tanımlama böylece `AND`, `OR`, `NOT` ve `XOR` bunlar üzerinde bit düzeyinde işlemler gerçekleştirilebilir. Bit bayrakları enum'da "hiçbir bayrakları ayarlanmış." anlamına gelen sıfır değerine sahip adlandırılmış bir sabit Ekle "Hiçbir bayrakları ayarlanmış" gelmez, bayrak sıfır değeri vermeyin.

Aşağıdaki örnekte, başka bir sürümü `Day` adlı sabit listesi `Days`, tanımlanır. `Days` sahip `Flags` özniteliği ve her bir değeri 2'in sonraki büyük güç atanır. Bu sayede oluşturmak bir `Days` değişken değeri `Days.Tuesday | Days.Thursday`.

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

Bir numaralandırma üzerinde bir bayrak belirlemek için mü kullanmak `OR` aşağıdaki örnekte gösterildiği bir işleç:

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

Belirli bir bayrağı ayarlanmış olup olmadığını belirlemek için bir mü kullanmak `AND` işlemi, aşağıdaki örnekte gösterildiği gibi:

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

Numaralandırma türleri ile tanımladığınızda göz önüne alınması gerekenler hakkında daha fazla bilgi için <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği için bkz: <xref:System.Enum?displayProperty=nameWithType>.

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a>Keşfedin ve sabit listesi değerlerinin işlemek için System.Enum yöntemlerini kullanma

Tüm numaralandırmalar örnekleridir <xref:System.Enum?displayProperty=nameWithType> türü. Yeni sınıflardan türetilemez <xref:System.Enum?displayProperty=nameWithType>, ancak enum örneği değerleri hakkında bilgi bulmak ve yöntemlerini kullanabilirsiniz.

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

Daha fazla bilgi için bkz. <xref:System.Enum?displayProperty=nameWithType>.

Bir genişletme yöntemi kullanarak, bir numaralandırma için yeni bir yöntem de oluşturabilirsiniz. Daha fazla bilgi için [nasıl yapılır: numaralandırma için yeni bir yöntem oluşturma](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Enum?displayProperty=nameWithType>  
- [C# Programlama Kılavuzu](../../csharp/programming-guide/index.md)  
- [enum](../../csharp/language-reference/keywords/enum.md)
