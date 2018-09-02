---
title: 'Nasıl yapılır: Özel bir Uzantı Metodu Uygulama ve Arama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 6b349876a60ad277ca933a4b4fbcbfffed2bd188
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452683"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Nasıl yapılır: Özel bir Uzantı Metodu Uygulama ve Arama (C# Programlama Kılavuzu)
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
  
 [!code-csharp[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi yapıştırın. Varsayılan olarak, bu proje 3.5 sürümünü hedefleyen [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve bir System.Core.dll başvurusu vardır ve bir `using` System.Linq yönergesi. Projeden bir veya daha fazla bu gereksinimleri eksikse, bunları el ile ekleyebilirsiniz.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Genişletme yöntemleri, belirli güvenlik güvenlik açığı var. Tüm ad çakışmalarını örneği veya türü tarafından tanımlanan statik yöntem ile değiştiriliyor çözümlenir çünkü bir türün varolan yöntemleri kimliğine bürünmek için hiç kullanılabilir. Genişletme yöntemleri, genişletilmiş sınıf özel tüm verileri erişemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genişletme Yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [LINQ (dil ile tümleşik sorgu)](../../../csharp/linq/linq-in-csharp.md)  
 [Statik Sınıflar ve Statik Sınıf Üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [this](../../../csharp/language-reference/keywords/this.md)  
 [namespace](../../../csharp/language-reference/keywords/namespace.md)
