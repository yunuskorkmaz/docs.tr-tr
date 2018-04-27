---
title: Erken ve Geç Bağlama (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 10ecc965fb6d728454b3af33a6e93b2d7dbc327d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="early-and-late-binding-visual-basic"></a>Erken ve Geç Bağlama (Visual Basic)
Visual Basic derleyici adlı bir işlem gerçekleştirir `binding` bir nesne bir nesne değişkenine atanan zaman. Bir nesne *erken bağlama* bildirilen belirli nesne türünde olması için ne zaman bir değişkene atanır. Erken bağlama nesnelerine bellek ayırabilir ve bir uygulama yürütülmeden önce diğer en iyi duruma getirme gerçekleştirmek derleyici izin verin. Örneğin, aşağıdaki kod parçası türünde olması için bir değişken bildirir <xref:System.IO.FileStream>:  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]  
  
 Çünkü <xref:System.IO.FileStream> belirli nesne türü, atanan örnek `FS` erken bağlama.  
  
 Bunun aksine, bir nesnedir *geç bağlama* ne zaman bir değişkene atanır bildirilen türünde olmasını `Object`. Bu tür nesneler herhangi bir nesne başvuruları tutmak ancak erken bağlama nesneleri avantajları çoğunu eksik. Örneğin, aşağıdaki kod parçası tarafından döndürülen nesne tutmak için bir nesne değişkeni bildirir `CreateObject` işlevi:  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]  
  
## <a name="advantages-of-early-binding"></a>Erken bağlama avantajları  
 Daha verimli uygulamaları verim önemli iyileştirmeler yapmak için derleyici izin verdiğinden, mümkün olduğunda, erken bağlama nesneleri kullanmanız gerekir. Erken bağlama nesneleri geç bağlama nesneleri önemli ölçüde daha hızlıdır ve kodunuzu okuyun ve tam olarak ne tür bir nesneleri kullanıldığından belirterek sürdürmek daha kolay hale. Erken bağlama başka bir avantajı olduğundan, otomatik kod tamamlama ve dinamik Yardım gibi kullanışlı özellikler olanak tanıdığı olduğu [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] tümleşik geliştirme ortamı (IDE) düzenleme gibi tam olarak hangi nesne türünü çalıştığınız belirleyebilir kod. Bir program derlendiğinde derleyici hatalarını raporlamak izin verdiği için erken bağlama sayısı ve önem derecesi çalışma zamanı hataları azaltır.  
  
> [!NOTE]
>  Geç bağlama yalnızca kullanılabilir olarak bildirilen tür üyeleri erişmek için `Public`. Üyelere erişme bildirilen `Friend` veya `Protected Friend` bir çalışma zamanı hatası oluşur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>  
 [Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
