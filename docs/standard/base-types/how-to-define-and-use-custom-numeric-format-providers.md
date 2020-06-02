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
ms.openlocfilehash: d12899fff7d9e6cb63728ba0b160b70fa2a41a1a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290519"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Nasıl yapılır: Özel Sayısal Biçim Sağlayıcıları Tanımlama ve Kullanma
.NET Framework sayısal değerlerin dize temsili üzerinde kapsamlı denetim elde etmenizi sağlar. Sayısal değerlerin biçimini özelleştirmek için aşağıdaki özellikleri destekler:  
  
- Sayıları dize gösterimlerine dönüştürmek için önceden tanımlanmış bir biçim kümesi sağlayan standart sayısal biçim dizeleri. Bunları parametresi olan, gibi herhangi bir sayısal biçimlendirme yöntemiyle kullanabilirsiniz <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> `format` . Ayrıntılar için bkz. [Standart sayısal biçim dizeleri](standard-numeric-format-strings.md).  
  
- Özel sayısal biçim belirticileri tanımlamak için birleştirilebilecek bir sembol kümesi sağlayan özel sayısal biçim dizeleri. Ayrıca, bir parametresi olan gibi herhangi bir sayısal biçimlendirme yöntemiyle de kullanılabilirler <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> `format` . Ayrıntılar için bkz. [özel sayısal biçim dizeleri](custom-numeric-format-strings.md).  
  
- <xref:System.Globalization.CultureInfo> <xref:System.Globalization.NumberFormatInfo> Sayısal değerlerin dize temsillerini görüntülerken kullanılan sembolleri ve biçim desenlerini tanımlayan özel veya nesneler. Bunları parametresi olan, gibi herhangi bir sayısal biçimlendirme yöntemiyle kullanabilirsiniz <xref:System.Int32.ToString%2A> `provider` . Genellikle, `provider` parametresi kültüre özgü biçimlendirmeyi belirtmek için kullanılır.  
  
 Bazı durumlarda (bir uygulamanın biçimli hesap numarası, kimlik numarası veya posta kodu görüntülemesi gerektiğinde), bu üç teknik uygun değildir. .NET Framework Ayrıca bir <xref:System.Globalization.CultureInfo> <xref:System.Globalization.NumberFormatInfo> sayısal değerin nasıl biçimlendirildiğini belirlemek için ne bir veya bir nesnesi olan bir biçimlendirme nesnesi tanımlamanızı da sağlar. Bu konu, böyle bir nesne uygulamak için adım adım yönergeler sağlar ve telefon numaralarını biçimlendiren bir örnek sağlar.  
  
### <a name="to-define-a-custom-format-provider"></a>Özel biçim sağlayıcısı tanımlamak için  
  
1. Ve arabirimlerini uygulayan bir sınıf tanımlayın <xref:System.IFormatProvider> <xref:System.ICustomFormatter> .  
  
2. Yöntemini uygulayın <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> . <xref:System.IFormatProvider.GetFormat%2A>, biçimlendirme yönteminin ( <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi gibi) özel biçimlendirme gerçekleştirmekten gerçekten sorumlu olan nesneyi almak için çağırdığı bir geri çağırma yöntemidir. Öğesinin tipik bir uygulanması <xref:System.IFormatProvider.GetFormat%2A> aşağıdakileri yapar:  
  
    1. <xref:System.Type>Yöntem parametresi olarak geçirilen nesnenin bir arabirimi temsil edip etmediğini belirler <xref:System.ICustomFormatter> .  
  
    2. Parametresi arabirimini temsil ediyorsa <xref:System.ICustomFormatter> , <xref:System.IFormatProvider.GetFormat%2A> <xref:System.ICustomFormatter> özel biçimlendirme sağlamaktan sorumlu arabirimi uygulayan bir nesne döndürür. Genellikle, özel biçimlendirme nesnesi kendisini döndürür.  
  
    3. Parametresi arabirimini temsil etmez <xref:System.ICustomFormatter> , <xref:System.IFormatProvider.GetFormat%2A> döndürür `null` .  
  
3. Yöntemini uygulayın <xref:System.ICustomFormatter.Format%2A> . Bu yöntem yöntemi tarafından çağrılır <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> ve bir sayının dize gösterimini döndürmekten sorumludur. Yöntemi uygulamak, genellikle aşağıdakileri içerir:  
  
    1. İsteğe bağlı olarak, yöntemin, parametreyi inceleyerek biçimlendirme hizmetleri sağlaması için meşru bir şekilde hedeflendiğini doğrulayın `provider` . Hem hem de uygulayan nesneleri biçimlendirmek <xref:System.IFormatProvider> için <xref:System.ICustomFormatter> , `provider` geçerli biçimlendirme nesnesi ile eşitlik için parametreyi test etmeyi de kapsar.  
  
    2. Biçimlendirme nesnesinin özel biçim belirticilerini destekleyip desteklemediğini belirleme. (Örneğin, "N" Biçim belirleyicisi bir ABD telefon numarasının NANP biçiminde çıkış olması gerektiğini belirtebilir ve bir "I", ITU-T önerisi E. 123 biçiminde bir çıktıyı gösterebilir.) Biçim belirticileri kullanılıyorsa, yöntemi belirli biçim belirticisini işlemelidir. Bu, parametresindeki yöntemine geçirilir `format` . Hiçbir tanımlayıcı yoksa, `format` parametresinin değeri olur <xref:System.String.Empty?displayProperty=nameWithType> .  
  
    3. Yöntemine parametre olarak geçirilen sayısal değeri alın `arg` . Dize gösterimine dönüştürmek için gereken tüm düzenlemeleri gerçekleştirin.  
  
    4. Parametresinin dize temsilini döndürün `arg` .  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Özel bir sayısal biçimlendirme nesnesi kullanmak için  
  
1. Özel biçimlendirme sınıfının yeni bir örneğini oluşturun.  
  
2. <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>Biçimlendirme yöntemini çağırın, özel biçimlendirme nesnesini, biçimlendirme belirticisini (veya <xref:System.String.Empty?displayProperty=nameWithType> biri kullanılmazsa) ve biçimlendirilecek sayısal değeri geçirerek.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `TelephoneFormatter` bir ABD telefon numarasını temsil eden bir SAYıYı NANP veya E. 123 biçimine dönüştüren adlı özel bir sayısal biçim sağlayıcısını tanımlar. Yöntemi iki biçim belirticilerini işler, "N" (NANP biçimini çıkarır) ve "I" (Uluslararası E. 123 biçimini verir).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Özel sayısal biçim sağlayıcısı yalnızca yöntemiyle birlikte kullanılabilir <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> . Tüm sayısal biçimlendirme yöntemlerinin (gibi `ToString` ), türü bir parametreye sahip diğer aşırı yüklemeler, <xref:System.IFormatProvider> <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulamayı <xref:System.Type> türü temsil eden bir nesne olarak iletir <xref:System.Globalization.NumberFormatInfo> . Sonuç olarak, yöntemin bir nesne döndürmesini bekler <xref:System.Globalization.NumberFormatInfo> . Değilse, özel sayısal biçim sağlayıcısı yok sayılır ve <xref:System.Globalization.NumberFormatInfo> geçerli kültür için nesnesi kendi yerine kullanılır. Örnekte `TelephoneFormatter.GetFormat` Yöntem, yöntem parametresini inceleyerek ve dışında `null` bir türü temsil ediyorsa, bir sayısal biçimlendirme yöntemine uygun şekilde geçirilme olasılığını işler <xref:System.ICustomFormatter> .  
  
 Özel bir sayısal biçim sağlayıcısı bir biçim belirticileri kümesini destekliyorsa, yöntem çağrısında kullanılan biçim öğesinde biçim belirticisi sağlanmadığında, varsayılan bir davranış sağladığınızdan emin olun <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> . Örnekte, "N" varsayılan biçim belirticisidir. Bu, bir sayının bir açık Biçim belirleyicisi sağlayarak biçimlendirilmiş bir telefon numarasına dönüştürülmesini sağlar. Aşağıdaki örnekte bu tür bir yöntem çağrısı gösterilmektedir.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Ancak, biçimlendirme belirticisi yoksa dönüştürmenin oluşmasına de izin verir. Aşağıdaki örnekte bu tür bir yöntem çağrısı gösterilmektedir.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Varsayılan biçim belirticisi tanımlanmamışsa, <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> .net 'in kodunuzun desteklemediği biçimlendirme sağlayabilmesi için yöntemi uygulamanız aşağıdaki gibi kod içermelidir.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 Bu örnekte, uygulayan yöntemi <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> yöntemi için bir geri çağırma yöntemi işlevi sunacak şekilde tasarlanmıştır <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> . Bu nedenle, `formatProvider` geçerli nesneye bir başvuru içerip içermediğini anlamak için parametresini inceler `TelephoneFormatter` . Ancak, yöntemi doğrudan koddan de çağrılabilir. Bu durumda, `formatProvider` <xref:System.Globalization.CultureInfo> <xref:System.Globalization.NumberFormatInfo> kültüre özgü biçimlendirme bilgileri sağlayan bir veya nesnesi sağlamak için parametresini kullanabilirsiniz.
