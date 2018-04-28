---
title: Dinamik Nesnelerle Çalışma (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f00c57107da5e6ea428e14964d8fa4a870bc96c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="9a009-102">Dinamik Nesnelerle Çalışma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a009-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="9a009-103">Dinamik nesneler sağlayan başka bir yolu dışında `Object` türüne çalışma zamanında bir nesneye geç bağlama.</span><span class="sxs-lookup"><span data-stu-id="9a009-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="9a009-104">Dinamik Nesne üye özellikleri ve yöntemleri gibi çalışma zamanında tanımlanan dinamik arabirimlerini kullanarak sunan <xref:System.Dynamic> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="9a009-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="9a009-105">Sınıflarda kullanabilirsiniz <xref:System.Dynamic> statik türü veya biçimi eşleşmeyen veri yapılarını iş nesneleri oluşturmak için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="9a009-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="9a009-106">IronPython ve IronRuby gibi dinamik dillerde tanımlanan dinamik nesneler de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a009-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="9a009-107">Dinamik nesneler oluşturmak veya bir dinamik dilinde tanımlandığı dinamik bir nesne kullanmak nasıl Göster örnekler için bkz: [izlenecek yol: dinamik nesneler oluşturma ve kullanma](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, veya <xref:System.Dynamic.ExpandoObject>.</span><span class="sxs-lookup"><span data-stu-id="9a009-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 <span data-ttu-id="9a009-108">Visual Basic bağlar nesnelere IronPython ve IronRuby gibi dinamik dilleri ve dinamik dil çalışma zamanı kullanarak <xref:System.Dynamic.IDynamicMetaObjectProvider> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9a009-108">Visual Basic binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="9a009-109">Uygulayan sınıflar örnekleri `IDynamicMetaObjectProvider` arabirimi <xref:System.Dynamic.DynamicObject> ve <xref:System.Dynamic.ExpandoObject> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="9a009-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="9a009-110">Geç bağlama çağrısı uygulayan bir nesneye yaptıysanız `IDynamicMetaObjectProvider` arabirimi, bu arabirimi kullanarak dinamik Nesne için Visual Basic bağlar.</span><span class="sxs-lookup"><span data-stu-id="9a009-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, Visual Basic binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="9a009-111">Geç bağlama çağrısı uygulamayan bir nesneye yapılırsa `IDynamicMetaObjectProvider` arabirimini veya çağrısı `IDynamicMetaObjectProvider` arabirimi başarısız olursa, Visual Basic, Visual Basic çalışma zamanı geç bağlama özelliklerini kullanarak nesnesine bağlar.</span><span class="sxs-lookup"><span data-stu-id="9a009-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, Visual Basic binds to the object by using the late-binding capabilities of the Visual Basic runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a009-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a009-112">See Also</span></span>  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [<span data-ttu-id="9a009-113">İzlenecek yol: Oluşturma ve dinamik nesneler kullanma</span><span class="sxs-lookup"><span data-stu-id="9a009-113">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [<span data-ttu-id="9a009-114">Erken ve Geç Bağlama</span><span class="sxs-lookup"><span data-stu-id="9a009-114">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
