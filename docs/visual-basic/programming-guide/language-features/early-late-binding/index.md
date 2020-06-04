---
title: Erken ve Geç Bağlama
ms.date: 07/20/2015
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
ms.openlocfilehash: e8d87e095b7c3104e3a2d66525644d1771ae883e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410637"
---
# <a name="early-and-late-binding-visual-basic"></a>Erken ve Geç Bağlama (Visual Basic)
Visual Basic derleyici bir nesne değişkenine bir nesne atandığında çağrılan bir işlem gerçekleştirir `binding` . Bir nesne, belirli bir nesne türü olarak belirtilen bir değişkene atandığında *erken bağlanır* . Erken bağlantılı nesneler, derleyicinin bellek ayırmasını ve uygulama yürütmeden önce diğer iyileştirmeler gerçekleştirmesini sağlar. Örneğin, aşağıdaki kod parçası türünde bir değişken bildirir <xref:System.IO.FileStream> :  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <xref:System.IO.FileStream>, Belirli bir nesne türü olduğundan, öğesine atanan örnek erken bir şekilde `FS` bağlanır.  
  
 Buna karşılık, bir nesne, türü olarak belirtilen bir değişkene atandığında *geç bağlanır* `Object` . Bu türdeki nesneler herhangi bir nesneye başvuruları tutabilir, ancak erken bağlantılı nesnelerin avantajlarından birçoğuna sahip olabilir. Örneğin, aşağıdaki kod parçası, işlev tarafından döndürülen bir nesneyi tutacak bir nesne değişkeni bildirir `CreateObject` :  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a>Erken bağlamanın avantajları  
 Derleyicinin daha verimli uygulamalar sunan önemli iyileştirmeler yapmasına izin verdiklerinden, mümkün olduğunda erken bağlanan nesneleri kullanmanız gerekir. Erken bağlantılı nesneler, geç bağlantılı nesnelerden önemli ölçüde daha hızlıdır ve tam olarak hangi tür nesnelerin kullanıldığını belirterek kodunuzun okunmasını ve bakımını daha kolay hale getirir. Erken bağlamanın bir diğer avantajı da, kodu düzenlerken Visual Studio tümleşik geliştirme ortamı (IDE) tam olarak ne tür bir nesne olduğunu belirleyebildiğinden otomatik kod tamamlama ve dinamik yardım gibi yararlı özelliklerden yararlanmasıdır. Erken bağlama, bir program derlendiğinde derleyicinin hata raporlenmesini sağladığından, çalışma zamanı hatalarının sayısını ve önem derecesini azaltır.  
  
> [!NOTE]
> Geç bağlama yalnızca, olarak belirtilen tür üyelerine erişmek için kullanılabilir `Public` . `Friend` `Protected Friend` Bir çalışma zamanı hatası olarak belirtilen üyelere erişme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme](../objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Nesne Veri Türü](../../../language-reference/data-types/object-data-type.md)
