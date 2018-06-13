---
title: Numaralandırma türleri (C# programlama Kılavuzu)
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: a97c3569899e7cf99dd522024de8373c60076571
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339059"
---
# <a name="enumeration-types-c-programming-guide"></a>Numaralandırma türleri (C# programlama Kılavuzu)

(Ayrıca bir sabit listesi veya bir enum adlı) bir numaralandırma türü bir değişkene atanabilir adlandırılmış tamsayı sabitleri kümesini tanımlamak için etkili bir yol sağlar. Örneğin, değeri haftanın gününü temsil edecek bir değişkeni tanımlamak olduğunu varsayalım. Bu değişken her zamankinden depolayacak yalnızca yedi anlamlı değerleri vardır. Bu değerleri tanımlamak için kullanarak bildirilmiş bir numaralandırma türü kullanabilirsiniz [enum](../../csharp/language-reference/keywords/enum.md) anahtar sözcüğü.

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

Varsayılan olarak temel alınan her bir öğesinde enum türünde [int](../../csharp/language-reference/keywords/int.md). Önceki örnekte gösterildiği gibi iki nokta kullanarak başka bir tam sayı sayısal tür belirtebilirsiniz. Olası türlerinin tam listesi için bkz: [enum (C# Başvurusu)](../../csharp/language-reference/keywords/enum.md).

Temel alınan sayısal değerler, aşağıdaki örnekte gösterildiği gibi temel alınan tür atama doğrulayabilirsiniz.

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

Enum yerine sayısal bir tür kullanmanın yararları şunlardır:

- Açıkça istemci kodu hangi değişken için geçerli değerler için belirtin.

- Visual Studio'da IntelliSense tanımlanan değerleri listeler.

Numaralandırıcı listedeki öğelerin değerlerini belirtmediğinde değerleri otomatik olarak 1 artırılır. Önceki örnekte, `Day.Sunday` 0 ' değerine sahip `Day.Monday` 1 ve benzeri bir değer içeriyor. Yeni bir oluşturduğunuzda `Day` nesnesi, varsayılan değer olan olacaktır `Day.Sunday` (0), açıkça, bir değer atamazsanız. Enum oluşturduğunuzda, en mantıklı varsayılan değer seçin ve sıfır değeri verin. Oluşturuldukları sırada açıkça bir değer atanmışlarsa değil, bu varsayılan değere sahip tüm numaralandırmaları neden.

Varsa değişkeni `meetingDay` türü `Day`, (açık atama) yalnızca bunu tarafından tanımlanan değerlerden biri atayabilirsiniz sonra `Day`. Ve toplantı gün değişse yeni bir değer atayabilirsiniz `Day` için `meetingDay`:

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> Herhangi bir rastgele tamsayı değerine atamak da mümkündür `meetingDay`. Örneğin, bu kod satırı hata üretmez: `meetingDay = (Day) 42`. Örtük beklenir bir enum değişken yalnızca enum tarafından tanımlanan değerlerden biri tutacak, çünkü ancak, bunu kullanmayın. Rastgele bir değeri bir numaralandırma türü değişkenine atamak için yüksek riskli hataları uygulamaktır.

Bir numaralandırma türünün Numaralandırıcı listesindeki öğeleri herhangi bir değeri atayabilir ve hesaplanan değerler de kullanabilirsiniz:

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a>Bit bayrakları olarak numaralandırma türleri

Bir numaralandırma türü, bit bayrakları tanımlamak için hangi Numaralandırıcı listesinde tanımlanan değerlerin herhangi bir birleşimini depolamak için numaralandırma türü örneğini etkinleştirir kullanabilirsiniz. (Doğal olarak, bazı birleşimleri anlamlı veya izin verilen program kodunuzda olmayabilir.)

Bit bayrakları enum uygulayarak oluşturun <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği ve değerleri uygun şekilde tanımlama böylece `AND`, `OR`, `NOT` ve `XOR` bit düzeyinde işlemler bunlar üzerinde gerçekleştirilebilir. Adlandırılmış bir sabit "hiçbir bayraklarını ayarlayın." anlamına gelir sıfır değeri ile bir bit bayrakları enum içindeki içerir "Hiçbir bayraklarını ayarlayın" gelmez, bir bayrak sıfır değeri vermeyin.

Aşağıdaki örnekte, başka bir sürümü `Day` adlı enum `Days`, tanımlanır. `Days` sahip `Flags` öznitelik ve her değer 2'in sonraki büyük üssü atanır. Bu oluşturmanızı sağlayan bir `Days` değişken değeri `Days.Tuesday | Days.Thursday`.

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

Enum üzerinde bir bayrak belirlemek için bitwise kullanmak `OR` aşağıdaki örnekte gösterildiği gibi işleci:

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

Belirli bir bayrağı ayarlanmış olup olmadığını belirlemek için bit kullanmak `AND` işlemi, aşağıdaki örnekte gösterildiği gibi:

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

Numaralandırma türleri ile tanımladığınızda dikkat edilmesi gerekenler hakkında daha fazla bilgi için <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği için bkz: <xref:System.Enum?displayProperty=nameWithType>.

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a>System.Enum yöntemleri kullanarak bulmak ve enum değerleri

Tüm numaralandırmaları örnekleridir <xref:System.Enum?displayProperty=nameWithType> türü. Yeni sınıflardan türetilemez <xref:System.Enum?displayProperty=nameWithType>, ancak kendi yöntemleri hakkında bilgi bulmak ve enum örneğindeki değerlerini değiştirmek için kullanabilirsiniz.

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

Daha fazla bilgi için bkz. <xref:System.Enum?displayProperty=nameWithType>.

Bir genişletme yöntemi kullanarak, bir numaralandırma için yeni bir yöntem de oluşturabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: numaralandırma için yeni bir yöntem oluşturma](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

## <a name="see-also"></a>Ayrıca bkz.
 <xref:System.Enum?displayProperty=nameWithType>  
 [C# Programlama Kılavuzu](../../csharp/programming-guide/index.md)  
 [enum](../../csharp/language-reference/keywords/enum.md)
