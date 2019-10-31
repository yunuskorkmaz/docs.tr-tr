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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140070"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Nasıl yapılır: Özel Sayısal Biçim Sağlayıcıları Tanımlama ve Kullanma
.NET Framework sayısal değerlerin dize temsili üzerinde kapsamlı denetim elde etmenizi sağlar. Sayısal değerlerin biçimini özelleştirmek için aşağıdaki özellikleri destekler:  
  
- Sayıları dize gösterimlerine dönüştürmek için önceden tanımlanmış bir biçim kümesi sağlayan standart sayısal biçim dizeleri. Bunları, `format` parametresine sahip <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>gibi herhangi bir sayısal biçimlendirme yöntemiyle kullanabilirsiniz. Ayrıntılar için bkz. [Standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
- Özel sayısal biçim belirticileri tanımlamak için birleştirilebilecek bir sembol kümesi sağlayan özel sayısal biçim dizeleri. Ayrıca, `format` parametresine sahip <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>gibi herhangi bir sayısal biçimlendirme yöntemiyle de kullanılabilir. Ayrıntılar için bkz. [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
- Sayısal değerlerin dize temsillerini görüntülerken kullanılan sembolleri ve biçim desenlerini tanımlayan özel <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.NumberFormatInfo> nesneleri. Bunları, `provider` parametresine sahip <xref:System.Int32.ToString%2A>gibi herhangi bir sayısal biçimlendirme yöntemiyle kullanabilirsiniz. Genellikle, `provider` parametresi kültüre özgü biçimlendirmeyi belirtmek için kullanılır.  
  
 Bazı durumlarda (bir uygulamanın biçimli hesap numarası, kimlik numarası veya posta kodu görüntülemesi gerektiğinde), bu üç teknik uygun değildir. .NET Framework Ayrıca bir sayısal değerin nasıl biçimlendirildiğini belirlemek için, bir <xref:System.Globalization.CultureInfo> ya da bir <xref:System.Globalization.NumberFormatInfo> nesnesi olan bir biçimlendirme nesnesi tanımlamanızı da sağlar. Bu konu, böyle bir nesne uygulamak için adım adım yönergeler sağlar ve telefon numaralarını biçimlendiren bir örnek sağlar.  
  
### <a name="to-define-a-custom-format-provider"></a>Özel biçim sağlayıcısı tanımlamak için  
  
1. <xref:System.IFormatProvider> ve <xref:System.ICustomFormatter> arabirimlerini uygulayan bir sınıf tanımlayın.  
  
2. <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yöntemini uygulayın. <xref:System.IFormatProvider.GetFormat%2A>, biçimlendirme yönteminin (<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi gibi) özel biçimlendirme gerçekleştirmekten gerçekten sorumlu olan nesneyi almak için çağırdığı bir geri çağırma yöntemidir. <xref:System.IFormatProvider.GetFormat%2A> tipik bir uygulama şunları yapar:  
  
    1. Yöntem parametresi olarak geçirilen <xref:System.Type> nesnesinin bir <xref:System.ICustomFormatter> arabirimini temsil edip etmediğini belirler.  
  
    2. Parametresi <xref:System.ICustomFormatter> arabirimini temsil ediyorsa, <xref:System.IFormatProvider.GetFormat%2A> özel biçimlendirme sağlamaktan sorumlu <xref:System.ICustomFormatter> arabirimini uygulayan bir nesne döndürür. Genellikle, özel biçimlendirme nesnesi kendisini döndürür.  
  
    3. Parametresi <xref:System.ICustomFormatter> arabirimini temsil etmediği <xref:System.IFormatProvider.GetFormat%2A> `null`döndürür.  
  
3. <xref:System.ICustomFormatter.Format%2A> yöntemini uygulayın. Bu yöntem <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi tarafından çağrılır ve bir sayının dize gösterimini döndürmekten sorumludur. Yöntemi uygulamak, genellikle aşağıdakileri içerir:  
  
    1. İsteğe bağlı olarak, yöntemin `provider` parametresini inceleyerek biçimlendirme Hizmetleri sağlamaya yönelik meşru bir şekilde sağlandığından emin olun. Hem <xref:System.IFormatProvider> hem de <xref:System.ICustomFormatter>uygulayan nesneleri biçimlendirmek için, bu, geçerli biçimlendirme nesnesiyle eşitlik için `provider` parametresinin test edilmesini içerir.  
  
    2. Biçimlendirme nesnesinin özel biçim belirticilerini destekleyip desteklemediğini belirleme. (Örneğin, "N" Biçim belirleyicisi bir ABD telefon numarasının NANP biçiminde çıkış olması gerektiğini belirtebilir ve bir "I", ITU-T önerisi E. 123 biçiminde bir çıktıyı gösterebilir.) Biçim belirticileri kullanılıyorsa, yöntemi belirli biçim belirticisini işlemelidir. `format` parametresindeki yöntemine geçirilir. Hiçbir tanımlayıcı yoksa, `format` parametresinin değeri <xref:System.String.Empty?displayProperty=nameWithType>.  
  
    3. Yöntemine `arg` parametresi olarak geçirilen sayısal değeri alın. Dize gösterimine dönüştürmek için gereken tüm düzenlemeleri gerçekleştirin.  
  
    4. `arg` parametresinin dize temsilini döndürün.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Özel bir sayısal biçimlendirme nesnesi kullanmak için  
  
1. Özel biçimlendirme sınıfının yeni bir örneğini oluşturun.  
  
2. <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> biçimlendirme yöntemini çağırın, özel biçimlendirme nesnesini, biçimlendirme belirticisini (veya biri kullanılmazsa <xref:System.String.Empty?displayProperty=nameWithType>) ve biçimlendirilecek sayısal değeri geçirerek.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ABD telefon numarasını temsil eden bir sayıyı NANP veya E. 123 biçimine dönüştüren `TelephoneFormatter` adlı özel bir sayısal biçim sağlayıcısını tanımlar. Yöntemi iki biçim belirticilerini işler, "N" (NANP biçimini çıkarır) ve "I" (Uluslararası E. 123 biçimini verir).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Özel sayısal biçim sağlayıcısı yalnızca <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemiyle birlikte kullanılabilir. Sayısal biçimlendirme yöntemlerinin (örneğin, `ToString`) <xref:System.IFormatProvider> türünde bir parametreye sahip diğer aşırı yüklemeleri, <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulamasını <xref:System.Globalization.NumberFormatInfo> türünü temsil eden bir <xref:System.Type> nesnesine iletir. Sonuç olarak, yöntemin <xref:System.Globalization.NumberFormatInfo> nesne döndürmesini bekler. Değilse, özel sayısal biçim sağlayıcısı yok sayılır ve geçerli kültür için <xref:System.Globalization.NumberFormatInfo> nesnesi onun yerine kullanılır. Örnekte `TelephoneFormatter.GetFormat` yöntemi, yöntem parametresini inceleyerek ve <xref:System.ICustomFormatter>dışında bir türü temsil ediyorsa `null` döndürerek bir sayısal biçimlendirme yöntemine uygun bir şekilde geçirilme olasılığını işler.  
  
 Özel bir sayısal biçim sağlayıcısı bir biçim belirticileri kümesini destekliyorsa, <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> Yöntem çağrısında kullanılan biçim öğesinde biçim belirticisi sağlanmadığında varsayılan bir davranış sağladığınızdan emin olun. Örnekte, "N" varsayılan biçim belirticisidir. Bu, bir sayının bir açık Biçim belirleyicisi sağlayarak biçimlendirilmiş bir telefon numarasına dönüştürülmesini sağlar. Aşağıdaki örnekte bu tür bir yöntem çağrısı gösterilmektedir.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Ancak, biçimlendirme belirticisi yoksa dönüştürmenin oluşmasına de izin verir. Aşağıdaki örnekte bu tür bir yöntem çağrısı gösterilmektedir.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Varsayılan biçim belirticisi tanımlanmamışsa, .NET 'in kodunuzun desteklemediği biçimlendirme sağlayabilmesi için <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> yöntemi uygulamanız aşağıdaki gibi kodu içermelidir.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 Bu örnekte, <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> uygulayan yöntemi <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi için bir geri çağırma yöntemi olarak kullanılmaya yöneliktir. Bu nedenle, geçerli `TelephoneFormatter` nesnesine bir başvuru içerip içermediğini anlamak için `formatProvider` parametresini inceler. Ancak, yöntemi doğrudan koddan de çağrılabilir. Bu durumda, kültüre özgü biçimlendirme bilgileri sağlayan bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.NumberFormatInfo> nesnesi sağlamak için `formatProvider` parametresini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
