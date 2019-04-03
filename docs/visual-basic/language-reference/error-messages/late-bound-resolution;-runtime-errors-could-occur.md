---
title: Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 4fe79c74b6ff634223a4f10d8c5dc54bb77571cc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822303"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="cec30-102">Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir</span><span class="sxs-lookup"><span data-stu-id="cec30-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="cec30-103">Bir nesne olması için bildirilen bir değişkene atanır [nesne veri türü](../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="cec30-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="cec30-104">Olarak bir değişken bildirdiğinizde `Object`, derleyici gerçekleştirmelidir *geç bağlama*, çalışma zamanında ek işlemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cec30-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="cec30-105">Olası çalışma zamanı hataları uygulamanızı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="cec30-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="cec30-106">Örneğin, atadığınız bir <xref:System.Windows.Forms.Form> için `Object` değişkeni ve erişmeyi deneyin <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> özelliği, çalışma zamanı oluşturur bir <xref:System.MemberAccessException> çünkü <xref:System.Windows.Forms.Form> sınıfı koymuyor bir `NameTable` özelliği.</span><span class="sxs-lookup"><span data-stu-id="cec30-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="cec30-107">Belirli bir türde olması için değişken bildirirseniz derleyici gerçekleştirebilirsiniz *erken bağlama* derleme zamanında.</span><span class="sxs-lookup"><span data-stu-id="cec30-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="cec30-108">Bu, Gelişmiş performans, belirli bir türün üyeleri ve kodunuzun okunabilirliği denetimli erişim sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="cec30-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="cec30-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="cec30-109">By default, this message is a warning.</span></span> <span data-ttu-id="cec30-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="cec30-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="cec30-111">**Hata Kimliği:** BC42017</span><span class="sxs-lookup"><span data-stu-id="cec30-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cec30-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="cec30-112">To correct this error</span></span>  
  
-   <span data-ttu-id="cec30-113">Mümkünse, belirli bir türde olması değişkeni bildirir.</span><span class="sxs-lookup"><span data-stu-id="cec30-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cec30-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cec30-114">See also</span></span>

- [<span data-ttu-id="cec30-115">Erken ve Geç Bağlama</span><span class="sxs-lookup"><span data-stu-id="cec30-115">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="cec30-116">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="cec30-116">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
