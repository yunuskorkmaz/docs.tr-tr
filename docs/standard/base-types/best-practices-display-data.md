---
title: .NET 'te veri görüntüleme ve kalıcı olarak biçimlendirilen veriler için en iyi uygulamalar
description: .NET uygulamalarında sayısal ve Tarih verisini etkin bir şekilde görüntülemeyi ve kalıcı yapmayı öğrenin.
ms.date: 05/01/2019
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.openlocfilehash: dd2e85ed695072da24b6b25b187810a109b89b25
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693130"
---
# <a name="best-practices-for-displaying-and-persisting-formatted-data"></a>Biçimlendirilen verileri görüntülemek ve kalıcı yapmak için en iyi uygulamalar

Bu makalede, sayısal veriler ve Tarih ve saat verileri gibi biçimlendirilen verilerin görüntüleme ve depolama için nasıl işlendiği incelenir.

.NET ile geliştirirken, bir kullanıcı arabiriminde sayı ve tarih gibi dize olmayan verileri göstermek için kültüre duyarlı biçimlendirme kullanın. Dize olmayan verileri dize biçiminde kalıcı hale getirmek için [sabit kültür](xref:System.Globalization.CultureInfo.InvariantCulture) ile biçimlendirme kullanın. Sayısal veya tarih ve saat verilerini dize biçiminde kalıcı hale getirmek için kültüre duyarlı biçimlendirme kullanmayın.

## <a name="displaying-formatted-data"></a>Biçimlendirilen verileri görüntüleme

Kullanıcılara sayılar ve tarih ve saatler gibi dize olmayan verileri görüntülerken bunları, kullanıcının kültürel ayarlarını kullanarak biçimlendirin. Varsayılan olarak, aşağıdaki hepsi biçimlendirme işlemlerinde geçerli iş parçacığı kültürünü kullanır:

- [C#](../../csharp/language-reference/tokens/interpolated.md) ve [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) derleyicileri tarafından desteklenen enterpolasyonlu dizeler.
- [C#](../../csharp/language-reference/operators/addition-operator.md#string-concatenation) veya [Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) birleştirme işleçlerini kullanan veya yöntemi doğrudan çağıran dize birleştirme işlemleri <xref:System.String.Concat%2A?displayProperty=nameWithType> .
- <xref:System.String.Format%2A?displayProperty=nameWithType>Yöntemi.
- `ToString`Sayısal türlerin ve Tarih ve saat türlerinin yöntemleri.

Bir dizenin belirlenen bir kültür veya [sabit kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)kuralları kullanılarak biçimlendirilmesi gerektiğini açıkça belirtmek için aşağıdakileri yapabilirsiniz:

- <xref:System.String.Format%2A?displayProperty=nameWithType>Ve yöntemlerini kullanırken, `ToString` veya gibi bir parametresi olan bir aşırı yüklemeyi çağırın `provider` <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği, <xref:System.Globalization.CultureInfo> istenen kültürü temsil eden bir örneği veya <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType> özelliği geçirin.

- Dize birleştirme için derleyicinin örtük dönüştürmeler gerçekleştirmesine izin vermeyin. Bunun yerine, parametresi olan bir aşırı yüklemeyi çağırarak açık bir dönüştürme gerçekleştirin `ToString` `provider` . Örneğin, derleyici bir <xref:System.Double> değeri aşağıdaki kodda bir dizeye dönüştürürken örtülü olarak geçerli kültürü kullanır:

  [!code-csharp[Implicit String Conversion](./snippets/best-practices-strings/csharp/tostring/Program.cs#1)]
  [!code-vb[Implicit String Conversion](./snippets/best-practices-strings/vb/tostring/Program.vb#1)]

  Bunun yerine, <xref:System.Double.ToString(System.IFormatProvider)?displayProperty=nameWithType> Aşağıdaki kod yaptığı gibi, yöntemini çağırarak, biçimlendirme kuralları dönüştürmede kullanılan kültürü açıkça belirtebilirsiniz:

  [!code-csharp[Explicit String Conversion](./snippets/best-practices-strings/csharp/tostring/Program.cs#2)]
  [!code-vb[Implicit String Conversion](./snippets/best-practices-strings/vb/tostring/Program.vb#2)]

- Dize ilişkilendirme için, bir örneğe bir enterpolasyonlu dize atamak yerine <xref:System.String> , ' a atayın <xref:System.FormattableString> . Daha sonra <xref:System.FormattableString.ToString?displayProperty=nameWithType> yöntemini çağırabilirsiniz, geçerli kültürün kurallarını yansıtan bir sonuç dizesi oluşturabilir veya <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> belirtilen bir kültürün kurallarını yansıtan bir sonuç dizesi oluşturmak için yöntemini çağırabilirsiniz. Ayrıca <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> , sabit kültürün kurallarını yansıtan bir sonuç dizesi üretmek için biçimlendirilebilir dizesini statik yönteme geçirebilirsiniz. Aşağıdaki örnek bu yaklaşımı gösterir. (Örneğin çıktısı, geçerli en-US kültürünü yansıtır.)

  [!code-csharp[String interpolation](./snippets/best-practices-strings/csharp/formattable/Program.cs)]
  [!code-vb[String interpolation](./snippets/best-practices-strings/vb/formattable/Program.vb)]

## <a name="persisting-formatted-data"></a>Kalıcı biçimli veriler

Dize olmayan verileri iki veri veya biçimlendirilmiş veri olarak kalıcı hale getirebilirsiniz. Eğer biçimlendirilmiş veri olarak kaydetmeyi seçerseniz, bir `provider` parametresi içeren bir biçimlendirme yöntemi aşırı yüklemesi çağırmanız ve <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliğini geçirmeniz gerekir. Sabit kültür, kültürden ve makineden bağımsız olan biçimlendirilmiş veriler için tutarlı bir biçim sağlar. Bunun aksine, sabit kültür dışındaki kültürler kullanılarak biçimlendirilen verileri kalıcı hale getirmenin birçok sınırlaması vardır:

- Veriler, farklı bir kültüre sahip sistemde alındığında veya geçerli sistemin kullanıcısı geçerli kültürü değiştirdiğinde ve verileri almaya çalıştığında bu verilerin kullanılamaz hale gelmesi muhtemeldir.
- Belirli bir bilgisayardaki kültürün özellikleri standart değerlerden farklı olabilir. Bir kullanıcı, istediği zaman kültüre duyarlı görüntüleme ayarlarını özelleştirebilir. Bu nedenle, bir sistemde kaydedilen biçimlendirilmiş veriler, kullanıcı kültürel ayarları özelleştirdikten sonra okunamaz hale gelebilir. Biçimlendirilmiş verilerin bilgisayarlar arası taşınabilirliğinin daha da sınırlı olması olasıdır.
- Sayıların veya tarih ve saatlerin biçimlendirmesini yöneten uluslararası, bölgesel veya ulusal standartlar zamanla değişir ve bu değişiklikler Windows işletim sistemi güncelleştirmelerine dahil edilir. Biçimlendirme kuralları değiştiğinde, önceki kurallar kullanılarak biçimlendirilen veriler okunamaz hale gelebilir.

Aşağıdaki örnek, veriyi kalıcı hale getirmek için kültüre duyarlı biçimlendirme kullanma sonucunda oluşan sınırlı taşınabilirliği gösterir. Örnek, bir tarih ve saat değerleri dizisini bir dosyaya kaydeder. Bu değerler, İngilizce (Amerika Birleşik Devletleri) kültürünün kuralları kullanılarak biçimlendirilir. Uygulama geçerli iş parçacığı kültürünü Fransızca (İsviçre) olarak değiştirdikten sonra, geçerli kültürün biçimlendirme kurallarını kullanarak kaydedilen değerleri okumaya çalışır. Veri öğelerinin ikisini okuma denemesi, bir <xref:System.FormatException> özel durumu oluşturur ve tarih dizisi artık <xref:System.DateTime.MinValue> değerine eşit olan iki yanlış öğeyi içerir.

[!code-csharp[Conceptual.Strings.BestPractices#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
[!code-vb[Conceptual.Strings.BestPractices#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]

Ancak, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> çağrılarındaki özelliğini ile değiştirirseniz, <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> aşağıdaki çıktıda gösterildiği gibi kalıcı tarih ve saat verileri başarıyla geri yüklenir:

```console
06.05.1758 21:26
05.05.1818 07:19
22.04.1870 23:54
08.09.1890 06:47
18.02.1905 15:12
```
