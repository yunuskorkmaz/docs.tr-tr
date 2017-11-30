---
title: "Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords: BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d01164914b484ef689654f048a8743f3c2eb669
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="6b361-102">Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir</span><span class="sxs-lookup"><span data-stu-id="6b361-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="6b361-103">Bir nesne olması için bildirilen bir değişkene atanır [nesne veri türü](../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="6b361-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="6b361-104">Bir değişken olarak bildirme zaman `Object`, derleyici gerçekleştirmelisiniz *geç bağlama*, çalışma zamanında ek işlemleri neden.</span><span class="sxs-lookup"><span data-stu-id="6b361-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="6b361-105">Olası çalışma zamanı hataları uygulamanıza kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="6b361-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="6b361-106">Örneğin, eğer atarsanız bir <xref:System.Windows.Forms.Form> için `Object` değişkeni ve erişmeyi deneyin <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> özelliği, çalışma zamanı oluşturur bir <xref:System.MemberAccessException> olduğundan <xref:System.Windows.Forms.Form> sınıfı uygulamaz bir `NameTable` özelliği.</span><span class="sxs-lookup"><span data-stu-id="6b361-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="6b361-107">Belirli bir türde olması için değişken bildirirseniz derleyici gerçekleştirebilirsiniz *erken bağlama* derleme zamanında.</span><span class="sxs-lookup"><span data-stu-id="6b361-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="6b361-108">Bu, Gelişmiş performans, belirli türün üyeleri ve okunabilirliği kodunuzun denetimli erişim sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="6b361-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="6b361-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="6b361-109">By default, this message is a warning.</span></span> <span data-ttu-id="6b361-110">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6b361-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="6b361-111">**Hata Kimliği:** BC42017</span><span class="sxs-lookup"><span data-stu-id="6b361-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6b361-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6b361-112">To correct this error</span></span>  
  
-   <span data-ttu-id="6b361-113">Mümkünse, belirli bir türde olması için değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="6b361-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b361-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b361-114">See Also</span></span>  
 [<span data-ttu-id="6b361-115">Erken ve geç bağlama</span><span class="sxs-lookup"><span data-stu-id="6b361-115">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [<span data-ttu-id="6b361-116">Nesne değişken bildirimi</span><span class="sxs-lookup"><span data-stu-id="6b361-116">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
