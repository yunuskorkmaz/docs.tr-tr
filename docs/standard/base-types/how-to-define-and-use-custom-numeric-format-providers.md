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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fab94c85745bf17a632d04c563070d79b48aa95
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318383"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Nasıl yapılır: Özel Sayısal Biçim Sağlayıcıları Tanımlama ve Kullanma
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Sayısal değerlerin dize gösterimini üzerinde kapsamlı denetim verir. Bu, sayısal değerlerin biçimini özelleştirmek için aşağıdaki özellikleri destekler:  
  
-   Standart sayısal biçim dizeleri, sayı, dize gösterimine dönüştürmek için önceden tanımlanmış birtakım biçimleri sağlar. Herhangi bir sayısal biçimlendirme yöntemi, aşağıdaki gibi kullanabilirsiniz <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, olan bir `format` parametresi. Ayrıntılar için bkz [standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
-   Simge kümesi sağlayan özel sayısal biçim dizeleri, özel sayısal biçim belirleyicilerinin tanımlamak için birleştirilebilir. Herhangi bir sayısal biçimlendirme yöntemi, gibi de kullanılabilir <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, olan bir `format` parametresi. Ayrıntılar için bkz [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
-   Özel <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.NumberFormatInfo> simgeleri tanımlamak ve biçimlendirme sayısal değerlerinin dize temsillerini görüntülenmesinde kullanılan desenleri, nesneleri. Herhangi bir sayısal biçimlendirme yöntemi, aşağıdaki gibi kullanabilirsiniz <xref:System.Int32.ToString%2A>, olan bir `provider` parametresi. Genellikle, `provider` parametresi kültüre özgü biçimlendirme belirtmek için kullanılır.  
  
 Bazı durumlarda (örneğin, bir uygulama biçimlendirilmiş hesap numarası, bir kimlik numarası veya posta kodu görüntüle gerekir) aşağıdaki üç tekniklerden uygun değildir. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Ayrıca ne bir biçimlendirme nesnesi tanımlamanızı sağlayan bir <xref:System.Globalization.CultureInfo> ya da bir <xref:System.Globalization.NumberFormatInfo> sayısal bir değer nasıl biçimlendirildiğini belirlemek için nesne. Bu konu, böyle bir nesnenin uygulamak için adım adım yönergeler sağlar ve telefon numaraları biçimlendiren bir örnek sağlar.  
  
### <a name="to-define-a-custom-format-provider"></a>Bir özel biçim sağlayıcısı tanımlamak için  
  
1. Uygulayan bir sınıf tanımlama <xref:System.IFormatProvider> ve <xref:System.ICustomFormatter> arabirimleri.  
  
2. Uygulama <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yöntemi. <xref:System.IFormatProvider.GetFormat%2A> bir geri çağırma yöntemi, biçimlendirme yöntemi (gibi <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi) aslında özel biçimlendirme yapmaktan sorumlu nesnesini almak için çağırır. Tipik bir uygulaması <xref:System.IFormatProvider.GetFormat%2A> şunları yapar:  
  
    1.  Belirler olmadığını <xref:System.Type> nesne bir yöntem olarak geçirilen parametreyi temsil eder bir <xref:System.ICustomFormatter> arabirimi.  
  
    2.  Parametresini temsil ediyorsa <xref:System.ICustomFormatter> arabirimi <xref:System.IFormatProvider.GetFormat%2A> uygulayan bir nesne döndürür <xref:System.ICustomFormatter> özel biçimlendirme sağlamaktan sorumluysa arabirimi. Genellikle, özel biçimlendirme nesnenin kendisini döndürür.  
  
    3.  Parametreyi temsil etmez, <xref:System.ICustomFormatter> arabirimi <xref:System.IFormatProvider.GetFormat%2A> döndürür `null`.  
  
3. Uygulama <xref:System.ICustomFormatter.Format%2A> yöntemi. Bu yöntemi çağıran <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi ve bir sayının dize gösterimini döndürmekten sorumludur. Yöntemi genellikle uygulama aşağıdakileri içerir:  
  
    1.  İsteğe bağlı olarak, yöntem inceleyerek biçimlendirme hizmetleri sağlamak için de avustralya'dan arama içindir emin `provider` parametresi. Her ikisi de uygulayan nesneler biçimlendirme <xref:System.IFormatProvider> ve <xref:System.ICustomFormatter>, bu testi içerir `provider` geçerli biçimlendirme nesne eşitliği parametresi.  
  
    2.  Özel biçim belirticileri biçimlendirme nesne desteklemesi gerekip gerekmediğini belirleyin. (Örneğin, bir "N" biçim belirticisi bir ABD telefon numarası çıktısı NANP biçiminde olmalıdır ve bir "ı" ITU-T öneri E.123 biçiminde çıktı gösterebilir gösterebilir.) Yöntem, biçim belirticileri kullandıysanız, özel Biçim belirleyicisi işlemesi gerekir. Yöntemine geçirilen `format` parametresi. Hiçbir tanımlayıcısı mevcutsa, değerini `format` parametresi <xref:System.String.Empty?displayProperty=nameWithType>.  
  
    3.  Geçirilen sayısal değer yöntemine alma `arg` parametresi. Hangi işlemeleri dize gösterimine dönüştürmek için gerekli olan gerçekleştirin.  
  
    4.  Dize temsilini döndürün `arg` parametresi.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Özel bir sayısal biçimlendirme nesnesini kullanmak için  
  
1. Özel biçimlendirme sınıfının yeni bir örneğini oluşturun.  
  
2. Çağrı <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> biçimlendirme yöntemi, özel biçimlendirme nesne biçimlendirme belirticisi geçirme (veya <xref:System.String.Empty?displayProperty=nameWithType>, bir kullanılmazsa) ve Biçimlendirilecek sayısal değer.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek adlı bir özel sayısal biçim sağlayıcısı tanımlar `TelephoneFormatter` kendi NANP veya E.123 biçimine bir ABD telefon numarasını temsil eden bir sayıya dönüştürür. Yöntemi iki biçim belirticileri, "(hangi NANP biçimi çıkışları) N" ve "I" (hangi uluslararası E.123 biçim çıkışları) işler.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Yalnızca özel sayısal biçim sağlayıcısı kullanılabilir <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi. Sayısal biçimlendirme yöntemleri, diğer aşırı yüklemeler (gibi `ToString`) türünde bir parametreye sahip <xref:System.IFormatProvider> tamamı pass <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulaması bir <xref:System.Type> temsil eden nesne <xref:System.Globalization.NumberFormatInfo> türü. Buna karşılık, döndürmek için yöntemin beklediği bir <xref:System.Globalization.NumberFormatInfo> nesne. Özel sayısal biçim sağlayıcısı kullanmıyorsa, göz ardı edilir ve <xref:System.Globalization.NumberFormatInfo> nesnesi geçerli kültürü onun yerine kullanılır. Örnekte, `TelephoneFormatter.GetFormat` yöntemi için yöntem parametresinde inceleme ve döndüren yöntemi biçimlendirme sayısal uygunsuz bir şekilde geçirilebilir olasılığını işler `null` dışındaki bir türü temsil ediyorsa <xref:System.ICustomFormatter>.  
  
 Özel sayısal biçim sağlayıcısı biçim belirticileri kümesi destekliyorsa, sağladığınız varsayılan davranışı kullanılan biçim öğesinde hiçbir biçim belirticisi sağlanmazsa emin <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntem çağrısı. Örnekte, "N" varsayılan biçim tanımlayıcısıdır. Bu bir açık biçim belirticisi sağlayarak biçimlendirilmiş telefon numarası için dönüştürülecek bir sayı sağlar. Aşağıdaki örnekte, böyle bir yöntem çağrısının gösterilmektedir.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Ancak dönüştürme hiçbir biçim belirticisi mevcut olduğunda için de sağlar. Aşağıdaki örnekte, böyle bir yöntem çağrısının gösterilmektedir.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Hiçbir varsayılan biçim tanımlayıcısı tanımlanmışsa, uygulamanıza <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> yöntemi, aşağıdaki gibi kod içermelidir, bu .NET biçimlendirme kodunuzu desteklemediği sağlayabilir.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 Bu örnekte, yöntem uygulayan <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> bir geri çağırma yöntemi olarak hizmet vermeye yönelik <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi. Bu nedenle, inceler `formatProvider` parametresi geçerli bir başvuru içerip içermediğini belirlemek için `TelephoneFormatter` nesne. Ancak, yöntem doğrudan koddan çağrılabilir. Bu durumda, kullanabileceğiniz `formatProvider` sağlamak için parametre bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.NumberFormatInfo> kültüre özgü biçimlendirme bilgileri sağlayan nesne.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu, csc.exe veya vb.exe kullanarak komut satırında derleyin. Visual Studio'da Kodu derlemek için bir konsol uygulaması projesi şablonu içine koyun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
