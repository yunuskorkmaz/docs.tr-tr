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
ms.openlocfilehash: bd70d8642c18e9bc2baba8128ec908c88e0477ce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345179"
---
# <a name="early-and-late-binding-visual-basic"></a>Erken ve Geç Bağlama (Visual Basic)
Visual Basic derleyici, nesne değişkenine bir nesne atandığında `binding` adlı bir işlem gerçekleştirir. Bir nesne, belirli bir nesne türü olarak belirtilen bir değişkene atandığında *erken bağlanır* . Erken bağlantılı nesneler, derleyicinin bellek ayırmasını ve uygulama yürütmeden önce diğer iyileştirmeler gerçekleştirmesini sağlar. Örneğin, aşağıdaki kod parçası <xref:System.IO.FileStream>türünde olması için bir değişken bildirir:  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <xref:System.IO.FileStream> belirli bir nesne türü olduğundan, `FS` atanan örnek erken bağlanır.  
  
 Buna karşılık, bir nesne, `Object`türünde olduğu belirtilen bir değişkene atandığında *geç bağlanır* . Bu türdeki nesneler herhangi bir nesneye başvuruları tutabilir, ancak erken bağlantılı nesnelerin avantajlarından birçoğuna sahip olabilir. Örneğin, aşağıdaki kod parçası `CreateObject` işlevi tarafından döndürülen bir nesneyi tutacak bir nesne değişkeni bildirir:  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a>Erken bağlamanın avantajları  
 Derleyicinin daha verimli uygulamalar sunan önemli iyileştirmeler yapmasına izin verdiklerinden, mümkün olduğunda erken bağlanan nesneleri kullanmanız gerekir. Erken bağlantılı nesneler, geç bağlantılı nesnelerden önemli ölçüde daha hızlıdır ve tam olarak hangi tür nesnelerin kullanıldığını belirterek kodunuzun okunmasını ve bakımını daha kolay hale getirir. Erken bağlamanın bir diğer avantajı da, Visual Studio tümleşik geliştirme ortamı (IDE), sizin düzenlediğiniz sırada çalıştığınız nesne türünü tam olarak belirleyebildiğinden, otomatik kod tamamlama ve dinamik yardım gibi faydalı özellikleri mümkün hale getirmenizi sağlar. kodudur. Erken bağlama, bir program derlendiğinde derleyicinin hata raporlenmesini sağladığından, çalışma zamanı hatalarının sayısını ve önem derecesini azaltır.  
  
> [!NOTE]
> Geç bağlama yalnızca `Public`olarak belirtilen tür üyelerine erişmek için kullanılabilir. `Friend` veya `Protected Friend` olarak belirtilen üyelere erişim bir çalışma zamanı hatasına neden olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
