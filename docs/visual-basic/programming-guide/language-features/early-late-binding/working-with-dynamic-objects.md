---
title: Dinamik Nesnelerle Çalışma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 78b17a379ea219cc24842322703caaa9d29eeb2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Dinamik Nesnelerle Çalışma (Visual Basic)
Dinamik nesneler sağlayan başka bir yolu dışında `Object` türüne çalışma zamanında bir nesneye geç bağlama. Dinamik Nesne üye özellikleri ve yöntemleri gibi çalışma zamanında tanımlanan dinamik arabirimlerini kullanarak sunan <xref:System.Dynamic> ad alanı. Sınıflarda kullanabilirsiniz <xref:System.Dynamic> statik türü veya biçimi eşleşmeyen veri yapılarını iş nesneleri oluşturmak için ad alanı. IronPython ve IronRuby gibi dinamik dillerde tanımlanan dinamik nesneler de kullanabilirsiniz. Dinamik nesneler oluşturmak veya bir dinamik dilinde tanımlandığı dinamik bir nesne kullanmak nasıl Göster örnekler için bkz: [izlenecek yol: dinamik nesneler oluşturma ve kullanma](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, veya <xref:System.Dynamic.ExpandoObject>.  
  
 Visual Basic bağlar nesnelere IronPython ve IronRuby gibi dinamik dilleri ve dinamik dil çalışma zamanı kullanarak <xref:System.Dynamic.IDynamicMetaObjectProvider> arabirimi. Uygulayan sınıflar örnekleri `IDynamicMetaObjectProvider` arabirimi <xref:System.Dynamic.DynamicObject> ve <xref:System.Dynamic.ExpandoObject> sınıfları.  
  
 Geç bağlama çağrısı uygulayan bir nesneye yaptıysanız `IDynamicMetaObjectProvider` arabirimi, bu arabirimi kullanarak dinamik Nesne için Visual Basic bağlar. Geç bağlama çağrısı uygulamayan bir nesneye yapılırsa `IDynamicMetaObjectProvider` arabirimini veya çağrısı `IDynamicMetaObjectProvider` arabirimi başarısız olursa, Visual Basic, Visual Basic çalışma zamanı geç bağlama özelliklerini kullanarak nesnesine bağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [İzlenecek yol: Oluşturma ve dinamik nesneler kullanma](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [Erken ve Geç Bağlama](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
