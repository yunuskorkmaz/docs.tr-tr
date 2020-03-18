---
title: 'Nasıl yapılır: Özel Sayısal Biçim Sağlayıcıları Tanımlama ve Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- custom numeric format strings
- numbers [.NET Framework], custom numeric format strings
- displaying date and time data
- format providers [.NET Framework]
- custom format strings
ms.assetid: a281bfbf-6596-45ed-a2d6-3782d535ada2
ms.openlocfilehash: 151bf40cf042517b7441b89688122373259dc7dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140070"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Nasıl yapılır: Özel Sayısal Biçim Sağlayıcıları Tanımlama ve Kullanma
.NET Framework, sayısal değerlerin dize gösterimi üzerinde kapsamlı bir denetim sağlar. Sayısal değerlerin biçimini özelleştirmek için aşağıdaki özellikleri destekler:  
  
- Sayıları dize gösterimlerine dönüştürmek için önceden tanımlanmış biçimler kümesi sağlayan standart sayısal biçim dizeleri. Parametresi olan <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> `format` sayısal biçimlendirme yöntemiyle kullanabilirsiniz. Ayrıntılar için [Standart Sayısal Biçim Dizeleri'ne](../../../docs/standard/base-types/standard-numeric-format-strings.md)bakın.  
  
- Özel sayısal biçim belirteçleri tanımlamak için birleştirilebilir semboller kümesi sağlayan özel sayısal biçim dizeleri. Parametresi olan <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> `format` sayısal biçimlendirme yöntemiyle de kullanılabilirler. Ayrıntılar için Bkz. [Özel Sayısal Biçim Dizeleri.](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
  
- Sayısal <xref:System.Globalization.CultureInfo> <xref:System.Globalization.NumberFormatInfo> değerlerin dize gösterimlerini gösterirken kullanılan sembolleri ve biçim desenlerini tanımlayan özel veya nesneler. Parametresi olan <xref:System.Int32.ToString%2A> `provider` sayısal biçimlendirme yöntemiyle kullanabilirsiniz. Genellikle, `provider` parametre kültüre özgü biçimlendirme belirtmek için kullanılır.  
  
 Bazı durumlarda (örneğin, bir uygulamanın biçimlendirilmiş bir hesap numarası, kimlik numarası veya posta kodu görüntülemesi gerektiği gibi) bu üç teknik uygun değildir. .NET Framework ayrıca sayısal bir değerin nasıl biçimlendiğini <xref:System.Globalization.CultureInfo> belirlemek <xref:System.Globalization.NumberFormatInfo> için ne bir ne de nesne olan bir biçimlendirme nesnesi tanımlamanızı sağlar. Bu konu, böyle bir nesneyi uygulamak için adım adım yönergeleri sağlar ve telefon numaralarını biçimlendiren bir örnek sağlar.  
  
### <a name="to-define-a-custom-format-provider"></a>Özel biçim sağlayıcısı tanımlamak için  
  
1. Arabirimleri ve arabirimleri uygulayan bir sınıf tanımlayın. <xref:System.IFormatProvider> <xref:System.ICustomFormatter>  
  
2. Yöntemi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulayın. <xref:System.IFormatProvider.GetFormat%2A>biçimlendirme yönteminin <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> (yöntem gibi) özel biçimlendirme gerçekleştirmekten gerçekten sorumlu olan nesneyi almak için çağırdığı bir geri arama yöntemidir. Tipik bir <xref:System.IFormatProvider.GetFormat%2A> uygulama aşağıdakileri yapar:  
  
    1. Yöntem parametresi olarak geçirilen nesnenin <xref:System.Type> <xref:System.ICustomFormatter> bir arabirimi temsil edip etmediğini belirler.  
  
    2. Parametre <xref:System.ICustomFormatter> arabirimi temsil ederse, <xref:System.IFormatProvider.GetFormat%2A> özel biçimlendirme <xref:System.ICustomFormatter> sağlamakla sorumlu arabirimi uygulayan bir nesne döndürür. Genellikle, özel biçimlendirme nesnesi kendi kendine döndürür.  
  
    3. Parametre arabirimi temsil <xref:System.ICustomFormatter> etmiyorsa, <xref:System.IFormatProvider.GetFormat%2A> döndürür. `null`  
  
3. Yöntemi <xref:System.ICustomFormatter.Format%2A> uygulayın. Bu yöntem <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntem tarafından çağrılır ve bir sayının dize gösterimini döndürmekten sorumludur. Yöntemin uygulanması genellikle aşağıdakileri içerir:  
  
    1. İsteğe bağlı olarak, yöntemin `provider` yasal olarak parametreyi inceleyerek biçimlendirme hizmetleri sağlamak amacıyla tasarlandıklarına emin olun. Her ikisini de <xref:System.IFormatProvider> <xref:System.ICustomFormatter>uygulayan nesneleri biçimlendirmek `provider` için bu, geçerli biçimlendirme nesnesiyle eşitlik için parametreyi sınama yı içerir.  
  
    2. Biçimlendirme nesnesinin özel biçim belirleyicilerini destekleyip desteklememesi gerektiğini belirleyin. (Örneğin, bir "N" biçim belirtici, bir ABD telefon numarasının NANP biçiminde çıktı olması gerektiğini gösterebilir ve "I" ITU-T Recommendation E.123 biçiminde çıktı gösterebilir.) Biçim belirteçleri kullanılırsa, yöntem belirli biçim belirtici işlemelidir. Parametredeki yönteme `format` aktarılır. Herhangi bir belirtim yoksa, `format` parametrenin değeri <xref:System.String.Empty?displayProperty=nameWithType>.  
  
    3. Yönteme `arg` parametre olarak geçen sayısal değeri alın. Dize gösterimine dönüştürmek için gereken tüm manipülasyonları gerçekleştirin.  
  
    4. Parametrenin dize `arg` gösterimini döndürün.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Özel sayısal biçimlendirme nesnesi kullanmak için  
  
1. Özel biçimlendirme sınıfının yeni bir örneğini oluşturun.  
  
2. Biçimlendirme <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemini çağırın, özel biçimlendirme nesnesini, biçimlendirme <xref:System.String.Empty?displayProperty=nameWithType>belirticisini (veya kullanılmamışsa) ve biçimlendirilecek sayısal değeri geçirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ABD telefon numarasını temsil `TelephoneFormatter` eden bir sayıyı NANP veya E.123 biçimine dönüştüren özel bir sayısal biçim sağlayıcısını tanımlar. Yöntem, "N" (NANP biçimini oluşturan) ve "I" (uluslararası E.123 biçimini çıkaran) olmak üzere iki biçim belirteçlerini işler.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Özel sayısal biçim sağlayıcısı yalnızca <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemle kullanılabilir. Bir `ToString`tür <xref:System.IFormatProvider> parametresi olan sayısal biçimlendirme yöntemlerinin (örneğin) diğer aşırı <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yükleri, uygulamanın <xref:System.Type> <xref:System.Globalization.NumberFormatInfo> türünü temsil eden bir nesneyi geçer. Buna karşılık, yöntemin bir <xref:System.Globalization.NumberFormatInfo> nesneyi döndürmesini beklerler. Yoksa, özel sayısal biçim sağlayıcısı yoksayılır ve geçerli <xref:System.Globalization.NumberFormatInfo> kültürün nesnesi onun yerine kullanılır. Örnekte, `TelephoneFormatter.GetFormat` yöntem, yöntem parametresini inceleyerek ve `null` <xref:System.ICustomFormatter>başka bir türü temsil ediyorsa döndürerek, uygun olmayan bir şekilde sayısal biçimlendirme yöntemine geçirilme olasılığını işler.  
  
 Özel bir sayısal biçim sağlayıcısı bir biçim belirtileyiciler kümesini destekliyorsa, <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntem çağrısında kullanılan biçim öğesinde biçim belirtici sağlanmışsa varsayılan bir davranış sağladığından emin olun. Örnekte, "N" varsayılan biçim belirtimidir. Bu, açık bir biçim belirtici sağlayarak bir sayının biçimlendirilmiş bir telefon numarasına dönüştürülmesine olanak tanır. Aşağıdaki örnekte böyle bir yöntem çağrısı gösteriş.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Ancak, biçim belirteci yoksa dönüştürmenin gerçekleşmesine de izin verir. Aşağıdaki örnekte böyle bir yöntem çağrısı gösteriş.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Varsayılan biçim belirtimi tanımlanmamışsa, <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> .NET'in kodunuzu desteklemediği biçimlendirmeyi sağlayabilmeleri için yöntemin uygulanmasınız aşağıdaki gibi kodlar içermelidir.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 Bu örnekte, uygulayan <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> yöntem yöntem için bir geri arama yöntemi olarak <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> hizmet etmek için tasarlanmıştır. Bu nedenle, geçerli `formatProvider` `TelephoneFormatter` nesneye bir başvuru içerip içermediğini belirlemek için parametreyi inceler. Ancak, yöntem doğrudan koddan da çağrılabilir. Bu durumda, kültüre `formatProvider` özgü biçimlendirme <xref:System.Globalization.CultureInfo> bilgileri <xref:System.Globalization.NumberFormatInfo> sağlayan bir veya nesne sağlamak için parametreyi kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
