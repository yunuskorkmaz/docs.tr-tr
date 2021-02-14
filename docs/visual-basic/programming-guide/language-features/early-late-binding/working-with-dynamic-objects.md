---
description: 'Hakkında daha fazla bilgi edinin: dinamik nesnelerle çalışma (Visual Basic)'
title: Dinamik Nesnelerle Çalışma
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 4991ae3deca908fc0b96760f50c85514df92714f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434400"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Dinamik Nesnelerle Çalışma (Visual Basic)

Dinamik nesneler, `Object` çalışma zamanında bir nesneye geç bağlamak için türü dışında başka bir yol sağlar. Dinamik bir nesne, ad alanında tanımlanan dinamik arabirimleri kullanarak çalışma zamanında Özellikler ve yöntemler gibi üyeleri ortaya koyar <xref:System.Dynamic> . <xref:System.Dynamic>Statik bir tür veya biçimle eşleşmeyen veri yapılarıyla çalışan nesneler oluşturmak için ad alanındaki sınıfları kullanabilirsiniz. Ayrıca, IronPython ve IronRuby gibi dinamik dillerde tanımlanmış dinamik nesneleri de kullanabilirsiniz. Dinamik nesneler oluşturmayı veya dinamik dilde tanımlanmış dinamik bir nesneyi kullanmayı gösteren örnekler için bkz. [Izlenecek yol: dinamik nesneler oluşturma ve kullanma](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject> veya kullanma <xref:System.Dynamic.ExpandoObject> .  
  
 Visual Basic, arabirimini kullanarak, dinamik dil çalışma zamanı ve IronPython ve IronRuby gibi dinamik dillerdeki nesnelere bağlanır <xref:System.Dynamic.IDynamicMetaObjectProvider> . Arabirimini uygulayan sınıfların örnekleri `IDynamicMetaObjectProvider` <xref:System.Dynamic.DynamicObject> ve <xref:System.Dynamic.ExpandoObject> sınıflarıdır.  
  
 Arabirimi uygulayan bir nesneye geç bağlanan bir çağrı yapılırsa `IDynamicMetaObjectProvider` Visual Basic, bu arabirimi kullanarak dinamik nesneye bağlanır. Arabirimi uygulamayan bir nesneye geç bağlama çağrısı yapılırsa `IDynamicMetaObjectProvider` veya arabirime yapılan çağrı `IDynamicMetaObjectProvider` başarısız olursa, Visual Basic çalışma zamanının geç bağlama yeteneklerini kullanarak nesneye bağlanır Visual Basic.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [İzlenecek yol: dinamik nesneler oluşturma ve kullanma](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [Erken ve geç bağlama](index.md)
