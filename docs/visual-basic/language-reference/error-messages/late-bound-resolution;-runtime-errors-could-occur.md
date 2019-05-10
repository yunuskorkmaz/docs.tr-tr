---
title: Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 6b78dfed1d615ba865f136365eac1c9c131ed5a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661942"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="a00c1-102">Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir</span><span class="sxs-lookup"><span data-stu-id="a00c1-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="a00c1-103">Bir nesne olması için bildirilen bir değişkene atanır [nesne veri türü](../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="a00c1-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="a00c1-104">Olarak bir değişken bildirdiğinizde `Object`, derleyici gerçekleştirmelidir *geç bağlama*, çalışma zamanında ek işlemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a00c1-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="a00c1-105">Olası çalışma zamanı hataları uygulamanızı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="a00c1-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="a00c1-106">Örneğin, atadığınız bir <xref:System.Windows.Forms.Form> için `Object` değişkeni ve erişmeyi deneyin <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> özelliği, çalışma zamanı oluşturur bir <xref:System.MemberAccessException> çünkü <xref:System.Windows.Forms.Form> sınıfı koymuyor bir `NameTable` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a00c1-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="a00c1-107">Belirli bir türde olması için değişken bildirirseniz derleyici gerçekleştirebilirsiniz *erken bağlama* derleme zamanında.</span><span class="sxs-lookup"><span data-stu-id="a00c1-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="a00c1-108">Bu, Gelişmiş performans, belirli bir türün üyeleri ve kodunuzun okunabilirliği denetimli erişim sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="a00c1-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="a00c1-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="a00c1-109">By default, this message is a warning.</span></span> <span data-ttu-id="a00c1-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a00c1-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="a00c1-111">**Hata Kimliği:** BC42017</span><span class="sxs-lookup"><span data-stu-id="a00c1-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a00c1-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a00c1-112">To correct this error</span></span>  
  
- <span data-ttu-id="a00c1-113">Mümkünse, belirli bir türde olması değişkeni bildirir.</span><span class="sxs-lookup"><span data-stu-id="a00c1-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00c1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a00c1-114">See also</span></span>

- [<span data-ttu-id="a00c1-115">Erken ve Geç Bağlama</span><span class="sxs-lookup"><span data-stu-id="a00c1-115">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="a00c1-116">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="a00c1-116">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
