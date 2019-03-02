---
title: 'Nasıl yapılır: Uygulama ve özel bir genişletme yöntemi - arama C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: e4b77bf0a44ce58db632e0c58982dba7178f9272
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203434"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Nasıl yapılır: Uygulama ve özel uzantı metodu çağırma (C# Programlama Kılavuzu)
Bu konu, kendi herhangi bir .NET türü için genişletme yöntemlerini gösterilmektedir. İstemci kodu, uzantı yöntemlerinizi kullanabilir, bunları içeren DLL bir başvuru eklemeyi ve ekleyerek bir [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergesi uzantı yöntemlerin tanımlandığı ad alanı belirtir.  
  
## <a name="to-define-and-call-the-extension-method"></a>Tanımlama ve uzantı metodu çağırma  
  
1.  Statik bir tanımlama [sınıfı](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) genişletme yöntemini içerecek.  
  
     Sınıfı için istemci kodu görünür olmalıdır. Erişilebilirlik kuralları hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
2.  En az bir genişletme yöntemi ile statik bir yöntem olarak uygulamak içeren sınıf olarak aynı görünürlük.  
  
3.  Yönteminin ilk parametresi, yöntemin işlediği türü belirtir. ile gelmelidir [bu](../../../csharp/language-reference/keywords/this.md) değiştiricisi.  
  
4.  Çağıran kodu ekleyin bir `using` belirtmek için yönergesi [ad alanı](../../../csharp/language-reference/keywords/namespace.md) uzantısı yöntemi sınıfı içeren.  
  
5.  Türün örnek yöntemleri değilmiş gibi yöntemler çağırır.  
  
     İşleç uygulanmakta türü temsil ettiğinden, kod çağırarak ilk parametre belirtilmedi ve derleyici, nesnenin türünü zaten bilir unutmayın. Yalnızca 2 parametrelerin bağımsız değişkenleri sağlamak zorunda `n`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte adlı bir uzantı yöntemini uygulayan `WordCount` içinde `CustomExtensions.StringExtension` sınıfı. Yöntemin işlediği <xref:System.String> ilk yöntem parametresi olarak belirtilen sınıf. `CustomExtensions` Ad alanı uygulama ad alanına aktarılır ve yöntem içinde çağrılır `Main` yöntemi.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi yapıştırın. Varsayılan olarak, bu proje 3.5 sürümünü hedefleyen [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve bir System.Core.dll başvurusu vardır ve bir `using` System.Linq yönergesi. Projeden bir veya daha fazla bu gereksinimleri eksikse, bunları el ile ekleyebilirsiniz.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Genişletme yöntemleri, belirli güvenlik güvenlik açığı var. Tüm ad çakışmalarını örneği veya türü tarafından tanımlanan statik yöntem ile değiştiriliyor çözümlenir çünkü bir türün varolan yöntemleri kimliğine bürünmek için hiç kullanılabilir. Genişletme yöntemleri, genişletilmiş sınıf özel tüm verileri erişemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Genişletme Yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [LINQ (dil ile tümleşik sorgu)](../../../csharp/linq/linq-in-csharp.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [protected](../../../csharp/language-reference/keywords/protected.md)
- [internal](../../../csharp/language-reference/keywords/internal.md)
- [public](../../../csharp/language-reference/keywords/public.md)
- [this](../../../csharp/language-reference/keywords/this.md)
- [namespace](../../../csharp/language-reference/keywords/namespace.md)
