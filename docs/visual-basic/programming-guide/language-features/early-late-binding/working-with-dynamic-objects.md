---
title: "Dinamik Nesnelerle Çalışma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da70c1e4c7398ad46d48c85b62ab884675bd1a73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Dinamik Nesnelerle Çalışma (Visual Basic)
Dinamik nesneler sağlayan başka bir yolu dışında `Object` türüne çalışma zamanında bir nesneye geç bağlama. Dinamik Nesne üye özellikleri ve yöntemleri gibi çalışma zamanında tanımlanan dinamik arabirimlerini kullanarak sunan <xref:System.Dynamic> ad alanı. Sınıflarda kullanabilirsiniz <xref:System.Dynamic> statik türü veya biçimi eşleşmeyen veri yapılarını iş nesneleri oluşturmak için ad alanı. IronPython ve IronRuby gibi dinamik dillerde tanımlanan dinamik nesneler de kullanabilirsiniz. Dinamik nesneler oluşturmak veya bir dinamik dilinde tanımlandığı dinamik bir nesne kullanmak nasıl Göster örnekler için bkz: [izlenecek yol: dinamik nesneler oluşturma ve kullanma](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, veya <xref:System.Dynamic.ExpandoObject>.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]kullanarak dinamik dil çalışma zamanı ve IronPython ve IronRuby gibi dinamik dilleri nesnelere bağlar <xref:System.Dynamic.IDynamicMetaObjectProvider> arabirimi. Uygulayan sınıflar örnekleri `IDynamicMetaObjectProvider` arabirimi <xref:System.Dynamic.DynamicObject> ve <xref:System.Dynamic.ExpandoObject> sınıfları.  
  
 Geç bağlama çağrısı uygulayan bir nesneye yaptıysanız `IDynamicMetaObjectProvider` arabirimi, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] arabirimi kullanarak dinamik Nesne bağlar. Geç bağlama çağrısı uygulamayan bir nesneye yapılırsa `IDynamicMetaObjectProvider` arabirimi veya çağrısı `IDynamicMetaObjectProvider` arabirimi başarısız [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] geç bağlama özelliklerini kullanarak nesnesine bağlar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] çalışma zamanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [İzlenecek yol: Oluşturma ve dinamik nesneler kullanma](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [Erken ve geç bağlama](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
