---
title: "Nasıl yapılır: Özel bir Uzantı Metodu Uygulama ve Arama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7de999c53f02fcc2bde4a8ccf504ba2b1d032638
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Nasıl yapılır: Özel bir Uzantı Metodu Uygulama ve Arama (C# Programlama Kılavuzu)
Bu konu, kendi içinde herhangi bir türü için genişletme yöntemleri uygulamak gösterilmiştir [.NET Framework sınıf kitaplığı](http://go.microsoft.com/fwlink/?LinkID=217856), veya genişletmek istediğiniz herhangi bir .NET türü. İstemci kodu, genişletme yöntemleri kullanabilir, bunları içeren DLL bir başvuru ekleyerek ve ekleyerek bir [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergesi genişletme yöntemleri tanımlanır ad alanını belirtir.  
  
## <a name="to-define-and-call-the-extension-method"></a>Tanımlama ve uzantı yöntemi çağırma  
  
1.  Statik tanımlamak [sınıfı](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) genişletme yöntemi içerecek şekilde.  
  
     Sınıfı için istemci kodu görünür olması gerekir. Erişilebilirlik kuralları hakkında daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
2.  En az genişletme yöntemi ile statik bir yöntem olarak uygulamak aynı görünürlük içeren sınıf.  
  
3.  Yönteminin ilk parametresi, yöntemin işlediği türünü belirtir; ile gelmelidir [bu](../../../csharp/language-reference/keywords/this.md) değiştiricisi.  
  
4.  Çağıran kodu ekleyin bir `using` belirtmek için yönergesi [ad alanı](../../../csharp/language-reference/keywords/namespace.md) uzantısı yöntemi sınıfı içerir.  
  
5.  Türün örnek yöntemleri değilmiş gibi yöntemlerini çağırın.  
  
     İlk parametre işleci uygulanmakta türünü temsil eder çünkü kodu çağırarak belirtilmemiş ve derleyici, nesne türü zaten bilir unutmayın. Yalnızca 2 parametreleriyle bağımsız değişkenleri sağlamak zorunda `n`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek adlı bir genişletme yöntemi uygulayan `WordCount` içinde `CustomExtensions.StringExtension` sınıfı. Yöntemin işlediği <xref:System.String> ilk yöntemi parametre olarak belirtilen sınıfı. `CustomExtensions` Uygulama ad alanına ad alanı içe aktarılan ve içinde çağrılan yöntemi `Main` yöntemi.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu çalıştırmak için kopyalamak ve içinde oluşturduğunuz bir Visual C# konsol uygulaması projesi yapıştırın [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)]. Varsayılan olarak, bu proje 3.5 sürümünü hedefler [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve System.Core.dll bir başvuru içeriyor ve bir `using` System.Linq yönergesi. Bir veya daha fazla bu gereksinimleri projeden eksikse, bunları el ile ekleyebilirsiniz.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Genişletme yöntemleri hiçbir belirli güvenlik açıkları sunar. Tüm ad çakışmaları örneği veya türü tarafından tanımlanan statik yöntemi lehinde çözümlenir çünkü bir türün varolan yöntemleri kimliğine bürünmek için hiçbir zaman kullanılabilir. Genişletme yöntemleri genişletilmiş sınıfındaki tüm özel verilere erişemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genişletme yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [Statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [korumalı](../../../csharp/language-reference/keywords/protected.md)  
 [İç](../../../csharp/language-reference/keywords/internal.md)  
 [Ortak](../../../csharp/language-reference/keywords/public.md)  
 [Bu](../../../csharp/language-reference/keywords/this.md)  
 [ad alanı](../../../csharp/language-reference/keywords/namespace.md)
