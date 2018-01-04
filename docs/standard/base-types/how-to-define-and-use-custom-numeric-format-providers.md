---
title: "Nasıl yapılır: Özel Sayısal Biçim Sağlayıcıları Tanımlama ve Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f8f06335d96b3e71f14b3df6b40ef3691c0915f1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Nasıl yapılır: Özel Sayısal Biçim Sağlayıcıları Tanımlama ve Kullanma
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Sayısal değerleri dize gösterimini üzerinde kapsamlı denetim sağlar. Sayısal değerler biçimini özelleştirmek için aşağıdaki özellikleri destekler:  
  
-   Standart sayısal biçim dizeleri, kendi dize gösterimi sayılara dönüştürme biçimleri önceden tanımlanmış bir kümesini sağlar. Tüm sayısal yöntemi gibi biçimlendirme ile kullanabilmek için <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, olan bir `format` parametresi. Ayrıntılar için bkz [standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
-   Özel sayısal biçim dizeleri, özel sayısal biçim belirticileri tanımlamak için birleştirilmiş simgeleri kümesi sağlar. Tüm sayısal yöntemi gibi biçimlendirme ile de kullanılabilir <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, olan bir `format` parametresi. Ayrıntılar için bkz [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
-   Özel <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.NumberFormatInfo> simgeleri tanımlayın ve biçimlendirme sayısal değerleri dize gösterimlerini görüntüleme kullanılan desenleri nesneleri. Tüm sayısal yöntemi gibi biçimlendirme ile kullanabilmek için <xref:System.Int32.ToString%2A>, olan bir `provider` parametresi. Genellikle, `provider` parametresi kültüre özgü biçimlendirme belirtmek için kullanılır.  
  
 Bazı durumlarda (örneğin, bir uygulama biçimlendirilmiş hesap numarası, bir kimlik numarası veya posta kodu görüntülediğinizde gerekir) bu üç teknikler uygunsuz. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Ne biçimlendirme bir nesne tanımlamanızı sağlayan bir <xref:System.Globalization.CultureInfo> ya da bir <xref:System.Globalization.NumberFormatInfo> bir sayısal değer nasıl biçimlendirilmiş belirlemek için nesne. Bu konu, böyle bir nesnenin uygulamak için adım adım yönergeler sağlar ve telefon numaraları biçimleri bir örnek sağlar.  
  
### <a name="to-define-a-custom-format-provider"></a>Özel biçim sağlayıcısı tanımlamak için  
  
1.  Arabirimini uygulayan bir sınıf tanımlama <xref:System.IFormatProvider> ve <xref:System.ICustomFormatter> arabirimleri.  
  
2.  Uygulama <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yöntemi. <xref:System.IFormatProvider.GetFormat%2A>bir geri çağırma yöntemi, biçimlendirme yöntemi (gibi <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi) gerçekte özel biçimlendirme gerçekleştirmek için sorumlu nesnesini almak için çağırır. Tipik bir uyarlamasını <xref:System.IFormatProvider.GetFormat%2A> şunları yapar:  
  
    1.  Belirler olup olmadığını <xref:System.Type> nesnesi geçirildi bir yöntem olarak parametre temsil eden bir <xref:System.ICustomFormatter> arabirimi.  
  
    2.  Parametre temsil ediyorsa <xref:System.ICustomFormatter> arabirimi, <xref:System.IFormatProvider.GetFormat%2A> uygulayan bir nesne döndürür <xref:System.ICustomFormatter> özel biçimlendirme sağlamaktan sorumludur arabirimi. Genellikle, özel biçimlendirme nesne kendisini döndürür.  
  
    3.  Parametre temsil etmez, <xref:System.ICustomFormatter> arabirimi, <xref:System.IFormatProvider.GetFormat%2A> döndürür `null`.  
  
3.  Uygulama <xref:System.ICustomFormatter.Format%2A> yöntemi. Bu yöntem tarafından çağrılır <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi ve bir numara dize gösterimini döndürmek için sorumludur. Yöntemi genellikle uygulama aşağıdakileri içerir:  
  
    1.  İsteğe bağlı olarak, yöntem inceleyerek biçimlendirme hizmetleri sağlamak için yasal olarak düşünüldüğünü emin olun `provider` parametresi. Her ikisi de uygulayan nesneler biçimlendirme <xref:System.IFormatProvider> ve <xref:System.ICustomFormatter>, bu sınama içerir `provider` parametresi geçerli biçimlendirme nesnesiyle eşitlik için.  
  
    2.  Biçimlendirme nesne özel biçim belirticileri desteklemesi gerekip gerekmediğini belirleyin. (Örneğin, bir "N" biçimi belirleyici bir ABD telefon numarası çıktısı NANP biçiminde olmalıdır ve bir "t" ITU-T öneri E.123 biçimde çıkış gösterebilir gösterebilir.) Biçim belirticiler kullandıysanız, yöntemi belirli biçim belirteci işlemelidir. Yöntemine geçirilen `format` parametresi. Hiçbir tanımlayıcısı varsa, değeri `format` parametresi <xref:System.String.Empty?displayProperty=nameWithType>.  
  
    3.  Geçirilen sayısal değer yöntemine alma `arg` parametresi. Ne olursa olsun işlemeleri kendi dize gösterimi dönüştürmek için gerekli olan gerçekleştirin.  
  
    4.  Dize gösterimini döndürür `arg` parametresi.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Özel sayısal biçimlendirme nesnesini kullanmak için  
  
1.  Özel biçimlendirme sınıfının yeni bir örneğini oluşturun.  
  
2.  Çağrı <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi biçimlendirme, özel biçimlendirme nesne biçimlendirme belirleyici geçirme (veya <xref:System.String.Empty?displayProperty=nameWithType>, bir kullanılmazsa) ve biçimlendirilmesi için sayısal değer.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek adlı bir özel sayısal biçim sağlayıcısı tanımlar `TelephoneFormatter` ABD telefon numarası, NANP veya E.123 biçimi temsil eden bir sayı dönüştürür. Yöntemi iki biçim belirticileri, "(NANP biçimi çıkarır) N" ve "I" (hangi uluslararası E.123 biçim çıkarır) işler.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Özel sayısal biçim sağlayıcısı yalnızca kullanılabilir <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi. Sayısal biçimlendirme yöntemlerine, diğer aşırı yüklemeler (gibi `ToString`) türünde bir parametreye sahip <xref:System.IFormatProvider> tüm geçirmek <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulaması bir <xref:System.Type> temsil eden nesne <xref:System.Globalization.NumberFormatInfo> türü. Buna karşılık, döndürmek için yöntemin bekledikleri bir <xref:System.Globalization.NumberFormatInfo> nesnesi. Özel sayısal biçim sağlayıcısı yoksa, göz ardı edilir ve <xref:System.Globalization.NumberFormatInfo> nesne geçerli kültürü onun yerine kullanılır. Örnekte, `TelephoneFormatter.GetFormat` yöntemi işler yöntemi yöntem parametresi incelenerek ve döndürme biçimlendirme sayısal açamayacağı geçirilebilir olasılığını `null` dışındaki bir türü temsil ediyorsa <xref:System.ICustomFormatter>.  
  
 Özel sayısal biçim sağlayıcı biçim belirticileri kümesi destekliyorsa, sağladığınız varsayılan davranışı kullanılan biçim öğesinde hiçbir biçim belirticisi sağlandıysa emin olun <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntem çağrısı. Örnekte, "N" varsayılan biçim belirticisi ' dir. Bu bir açık biçim belirticisi sağlayarak bir biçimlendirilmiş telefon numarası dönüştürülecek sayısını sağlar. Aşağıdaki örnek, bu tür bir yöntem çağrısı gösterilmektedir.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Ancak hiçbir biçim belirticisi mevcut olduğunda dönüştürme de sağlar. Aşağıdaki örnek, bu tür bir yöntem çağrısı gösterilmektedir.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Hiçbir varsayılan biçim belirticisi tanımlanırsa, uygulamanıza <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> yöntemi, aşağıdaki gibi kod içermelidir, .NET biçimlendirme kodunuzu desteklemediği sağlayabilir.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 Bu örnekte, yöntem uygulayan <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> bir geri çağırma yöntemi olarak hizmet vermeye yönelik <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi. Bu nedenle, inceler `formatProvider` parametresi geçerli bir başvuru içerip içermediğini belirlemek için `TelephoneFormatter` nesnesi. Ancak, yöntem doğrudan kodunuzdan çağrılabilir. Bu durumda, kullanabileceğiniz `formatProvider` sağlamak için parametre bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.NumberFormatInfo> kültüre özgü biçimlendirme bilgileri sağlayan nesne.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu, csc.exe veya vb.exe kullanarak komut satırında derleyin. Kodu [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] içinde derlemek için, bir konsol uygulaması projesi şablonu içine koyun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
