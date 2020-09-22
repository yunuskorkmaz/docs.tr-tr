---
title: Tanımlayıcı çok uzun
ms.date: 07/20/2015
f1_keywords:
- bc30033
- vbc30033
helpviewer_keywords:
- BC30033
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
ms.openlocfilehash: 084e3d9306ad84d7e6e36e5fe4bbfc868b8dfac6
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874010"
---
# <a name="identifier-is-too-long"></a><span data-ttu-id="bf5c8-102">Tanımlayıcı çok uzun</span><span class="sxs-lookup"><span data-stu-id="bf5c8-102">Identifier is too long</span></span>

<span data-ttu-id="bf5c8-103">Her programlama öğesinin adı veya tanımlayıcı 1023 karakterle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf5c8-103">The name, or identifier, of every programming element is limited to 1023 characters.</span></span> <span data-ttu-id="bf5c8-104">Ayrıca, tam nitelikli ad 1023 karakterden uzun olamaz.</span><span class="sxs-lookup"><span data-stu-id="bf5c8-104">In addition, a fully qualified name cannot exceed 1023 characters.</span></span> <span data-ttu-id="bf5c8-105">Bu, tüm tanımlayıcı dizesinin ( `<namespace>.<...>.<namespace>.<class>.<element>` ), üye erişim işleci () karakterleri dahil 1023 karakterden uzun olamayacağı anlamına gelir `.` .</span><span class="sxs-lookup"><span data-stu-id="bf5c8-105">This means that the entire identifier string (`<namespace>.<...>.<namespace>.<class>.<element>`) cannot be more than 1023 characters long, including the member-access operator (`.`) characters.</span></span>  
  
 <span data-ttu-id="bf5c8-106">**Hata kimliği:** BC30033</span><span class="sxs-lookup"><span data-stu-id="bf5c8-106">**Error ID:** BC30033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bf5c8-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="bf5c8-107">To correct this error</span></span>  
  
- <span data-ttu-id="bf5c8-108">Tanımlayıcının uzunluğunu azaltın.</span><span class="sxs-lookup"><span data-stu-id="bf5c8-108">Reduce the length of the identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5c8-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf5c8-109">See also</span></span>

- [<span data-ttu-id="bf5c8-110">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="bf5c8-110">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
