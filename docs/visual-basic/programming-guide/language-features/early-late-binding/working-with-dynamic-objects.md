---
title: Dinamik Nesnelerle Çalışma
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 20d007fb48e1db352bab6d8e25d2e60e02554732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345172"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Dinamik Nesnelerle Çalışma (Visual Basic)
Dinamik nesneler, çalışma zamanında bir nesneye geç bağlamak için `Object` türü dışında başka bir yol sağlar. Dinamik bir nesne, <xref:System.Dynamic> ad alanında tanımlanan dinamik arabirimleri kullanarak çalışma zamanında Özellikler ve yöntemler gibi üyeleri ortaya koyar. Statik bir tür veya biçimle eşleşmeyen veri yapılarıyla çalışan nesneler oluşturmak için <xref:System.Dynamic> ad alanındaki sınıfları kullanabilirsiniz. Ayrıca, IronPython ve IronRuby gibi dinamik dillerde tanımlanmış dinamik nesneleri de kullanabilirsiniz. Dinamik nesneler oluşturmayı veya dinamik dilde tanımlanmış dinamik bir nesneyi kullanmayı gösteren örnekler için bkz. [Izlenecek yol: dinamik nesneler oluşturma ve kullanma](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>veya <xref:System.Dynamic.ExpandoObject>.  
  
 Visual Basic, <xref:System.Dynamic.IDynamicMetaObjectProvider> arabirimini kullanarak, dinamik dil çalışma zamanı ve IronPython ve IronRuby gibi dinamik dillerdeki nesnelere bağlanır. `IDynamicMetaObjectProvider` arabirimini uygulayan sınıfların örnekleri <xref:System.Dynamic.DynamicObject> ve <xref:System.Dynamic.ExpandoObject> sınıflarıdır.  
  
 `IDynamicMetaObjectProvider` arabirimini uygulayan bir nesneye geç bağlı bir çağrı yapılırsa, Visual Basic bu arabirimi kullanarak dinamik nesneye bağlanır. `IDynamicMetaObjectProvider` arabirimini uygulamayan bir nesneye geç bağlı bir çağrı yapılırsa veya `IDynamicMetaObjectProvider` arabirimine yapılan çağrı başarısız olursa, Visual Basic çalışma zamanının geç bağlama yeteneklerini kullanarak nesneye bağlar Visual Basic.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [İzlenecek yol: dinamik nesneler oluşturma ve kullanma](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [Erken ve Geç Bağlama](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
