---
description: 'Daha fazla bilgi edinin: BC42017: geç bağlantılı çözüm; çalışma zamanı hataları oluşabilir'
title: Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 2c783a7aff46df8ab033463f49c45f4c797220ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795930"
---
# <a name="bc42017-late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="78072-103">BC42017: geç bağlantılı çözüm; çalışma zamanı hataları oluşabilir</span><span class="sxs-lookup"><span data-stu-id="78072-103">BC42017: Late bound resolution; runtime errors could occur</span></span>

<span data-ttu-id="78072-104">Nesne [veri türü](../data-types/object-data-type.md)olarak belirtilen bir değişkene bir nesne atanır.</span><span class="sxs-lookup"><span data-stu-id="78072-104">An object is assigned to a variable declared to be of the [Object Data Type](../data-types/object-data-type.md).</span></span>

 <span data-ttu-id="78072-105">Olarak bir değişken bildirdiğinizde `Object` , derleyicinin *geç bağlama* gerçekleştirmesi gerekir ve bu, çalışma zamanında ek işlemlere neden olur.</span><span class="sxs-lookup"><span data-stu-id="78072-105">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="78072-106">Ayrıca, uygulamanızı olası çalışma zamanı hatalarına da sunar.</span><span class="sxs-lookup"><span data-stu-id="78072-106">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="78072-107">Örneğin, değişkenine bir atar <xref:System.Windows.Forms.Form> `Object` ve sonra özelliğe erişmeyi denerseniz <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> , <xref:System.MemberAccessException> sınıf bir <xref:System.Windows.Forms.Form> özelliği kullanıma sunmadığından çalışma zamanı bir oluşturur `NameTable` .</span><span class="sxs-lookup"><span data-stu-id="78072-107">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>

 <span data-ttu-id="78072-108">Değişkeni belirli bir türde olacak şekilde bildirirseniz, derleyici derleme zamanında *erken bağlama* gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="78072-108">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="78072-109">Bu, belirli türde üyelere gelişmiş performans, denetimli erişim ve kodunuzun daha iyi okunmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="78072-109">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>

 <span data-ttu-id="78072-110">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="78072-110">By default, this message is a warning.</span></span> <span data-ttu-id="78072-111">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="78072-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="78072-112">**Hata kimliği:** BC42017</span><span class="sxs-lookup"><span data-stu-id="78072-112">**Error ID:** BC42017</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="78072-113">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="78072-113">To correct this error</span></span>

- <span data-ttu-id="78072-114">Mümkünse, değişkeni belirli bir türde olacak şekilde bildirin.</span><span class="sxs-lookup"><span data-stu-id="78072-114">If possible, declare the variable to be of a specific type.</span></span>

## <a name="see-also"></a><span data-ttu-id="78072-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78072-115">See also</span></span>

- [<span data-ttu-id="78072-116">Erken ve geç bağlama</span><span class="sxs-lookup"><span data-stu-id="78072-116">Early and Late Binding</span></span>](../../programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="78072-117">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="78072-117">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
