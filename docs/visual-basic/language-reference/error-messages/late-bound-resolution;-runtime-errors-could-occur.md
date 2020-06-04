---
title: Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: f1dc656a09eee05080356892b280a79505f3b9cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397356"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="2e546-102">Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir</span><span class="sxs-lookup"><span data-stu-id="2e546-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="2e546-103">Nesne [veri türü](../data-types/object-data-type.md)olarak belirtilen bir değişkene bir nesne atanır.</span><span class="sxs-lookup"><span data-stu-id="2e546-103">An object is assigned to a variable declared to be of the [Object Data Type](../data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="2e546-104">Olarak bir değişken bildirdiğinizde `Object` , derleyicinin *geç bağlama*gerçekleştirmesi gerekir ve bu, çalışma zamanında ek işlemlere neden olur.</span><span class="sxs-lookup"><span data-stu-id="2e546-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="2e546-105">Ayrıca, uygulamanızı olası çalışma zamanı hatalarına da sunar.</span><span class="sxs-lookup"><span data-stu-id="2e546-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="2e546-106">Örneğin, değişkenine bir atar <xref:System.Windows.Forms.Form> `Object` ve sonra özelliğe erişmeyi denerseniz <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> , <xref:System.MemberAccessException> sınıf bir <xref:System.Windows.Forms.Form> özelliği kullanıma sunmadığından çalışma zamanı bir oluşturur `NameTable` .</span><span class="sxs-lookup"><span data-stu-id="2e546-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="2e546-107">Değişkeni belirli bir türde olacak şekilde bildirirseniz, derleyici derleme zamanında *erken bağlama* gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2e546-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="2e546-108">Bu, belirli türde üyelere gelişmiş performans, denetimli erişim ve kodunuzun daha iyi okunmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2e546-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="2e546-109">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="2e546-109">By default, this message is a warning.</span></span> <span data-ttu-id="2e546-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2e546-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2e546-111">**Hata kimliği:** BC42017</span><span class="sxs-lookup"><span data-stu-id="2e546-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2e546-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2e546-112">To correct this error</span></span>  
  
- <span data-ttu-id="2e546-113">Mümkünse, değişkeni belirli bir türde olacak şekilde bildirin.</span><span class="sxs-lookup"><span data-stu-id="2e546-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e546-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e546-114">See also</span></span>

- [<span data-ttu-id="2e546-115">Erken ve geç bağlama</span><span class="sxs-lookup"><span data-stu-id="2e546-115">Early and Late Binding</span></span>](../../programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="2e546-116">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="2e546-116">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
