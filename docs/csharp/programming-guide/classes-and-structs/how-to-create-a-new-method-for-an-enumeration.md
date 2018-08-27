---
title: 'Nasıl yapılır: Numaralandırma için Yeni bir Yöntem Oluşturma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 8de44cbddf26af45245709d0e28d2d157256ce59
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932221"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Nasıl yapılır: Numaralandırma için Yeni bir Yöntem Oluşturma (C# Programlama Kılavuzu)
Belirli numaralandırma türüne özgü işlevsellik eklemek için genişletme yöntemleri kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `Grades` numaralandırması bir öğrenci bir sınıfta alabileceğiniz olası harf dereceleri temsil eder. Adlı bir genişletme yöntemi `Passing` eklenir `Grades` artık o türün her örneğinin "ya da değil, geçirme sınıf temsil edip etmediğini bilebilmesi" yazın.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 Unutmayın `Extensions` sınıfı ayrıca dinamik olarak güncelleştirilen bir statik değişken içerir ve dönüş değeri genişletme yöntemi bu değişkenin geçerli değeri yansıtır. Bu, arka planda, bunlar tanımlanır doğrudan statik sınıf üzerinde genişletme yöntemleri çağrılır, gösterir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi yapıştırın. Varsayılan olarak, bu proje 3.5 sürümünü hedefleyen [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve bir System.Core.dll başvurusu vardır ve bir `using` System.Linq yönergesi. Projeden bir veya daha fazla bu gereksinimleri eksikse, bunları el ile ekleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genişletme Yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
