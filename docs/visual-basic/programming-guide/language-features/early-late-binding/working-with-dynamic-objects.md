---
title: Dinamik Nesnelerle Çalışma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: ea7d7aae1cd79a0243a9c721b5e3958fba82f84f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832080"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Dinamik Nesnelerle Çalışma (Visual Basic)
Dinamik nesneler sağlayan başka bir deyişle, dışındaki `Object` türüne, nesneye geç bağlama çalışma zamanında. Dinamik Nesne, tanımlanan dinamik arabirimleri kullanarak çalışma zamanında özellikler ve yöntemler gibi üyeleri sunan <xref:System.Dynamic> ad alanı. Sınıfları kullanabilirsiniz <xref:System.Dynamic> bir statik türü veya biçimi eşleşmeyen veri yapıları ile çalışma nesneleri oluşturmak için ad alanı. IronPython ve Ironruby gibi dinamik dilleri tanımlanan dinamik nesneler de kullanabilirsiniz. Dinamik nesneler oluşturma veya dinamik dilinde tanımlandığı bir dinamik nesnesini gösteren örnekler için bkz: [izlenecek yol: Dinamik nesneler oluşturma ve kullanma](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, veya <xref:System.Dynamic.ExpandoObject>.  
  
 Visual Basic bağlar nesnelere dinamik dil çalışma zamanı ve IronPython ve Ironruby gibi dinamik dilleri kullanarak <xref:System.Dynamic.IDynamicMetaObjectProvider> arabirimi. Uygulayan sınıflar örnekleri `IDynamicMetaObjectProvider` arabirimi <xref:System.Dynamic.DynamicObject> ve <xref:System.Dynamic.ExpandoObject> sınıfları.  
  
 Geç bağlama çağrı uygulayan bir nesne için yapılması durumunda `IDynamicMetaObjectProvider` arabirim, o arabirimini kullanarak dinamik nesnesine Visual Basic bağlar. Uygulamayan bir nesneye bir geç bağlanan çağrı yapılırsa `IDynamicMetaObjectProvider` arabirimi veya çağrı `IDynamicMetaObjectProvider` arabirimi başarısız olursa, Visual Basic, Visual Basic çalışma zamanı geç bağlama özellikleri kullanarak nesnesine bağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [İzlenecek yol: Dinamik nesneler oluşturma ve kullanma](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [Erken ve Geç Bağlama](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
