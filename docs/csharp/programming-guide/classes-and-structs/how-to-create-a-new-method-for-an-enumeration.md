---
title: "Nasıl yapılır: Numaralandırma için Yeni bir Yöntem Oluşturma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3cc15d24c9ba954a19fb87d4e364ac6e7f78e8b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Nasıl yapılır: Numaralandırma için Yeni bir Yöntem Oluşturma (C# Programlama Kılavuzu)
Belirli numaralandırma türü için özel işlevsellik eklemek için genişletme yöntemleri kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `Grades` numaralandırma öğrencinin bir sınıfta alabilirsiniz olası harf dereceleri temsil eder. Adlı bir genişletme yöntemi `Passing` eklenen `Grades` türü artık her örneği bilir"veya değil, geçirme düzeyde temsil edip etmediğini böylece" yazın.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 Unutmayın `Extensions` sınıfı ayrıca dinamik olarak güncelleştirilen bir statik değişken içerir ve uzantı yönteminin dönüş değeri bu değişkenin geçerli değeri yansıtır. Bu arka planda tanımlı doğrudan statik sınıf üzerinde genişletme yöntemleri çağrılır, gösterir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu çalıştırmak için kopyalamak ve içinde oluşturduğunuz bir Visual C# konsol uygulaması projesi yapıştırın [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)]. Varsayılan olarak, bu proje 3.5 sürümünü hedefler [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve System.Core.dll bir başvuru içeriyor ve bir `using` System.Linq yönergesi. Bir veya daha fazla bu gereksinimleri projeden eksikse, bunları el ile ekleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genişletme yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
