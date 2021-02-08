---
description: 'Hakkında daha fazla bilgi edinin: BC30033: tanımlayıcı çok uzun'
title: Tanımlayıcı çok uzun
ms.date: 07/20/2015
f1_keywords:
- bc30033
- vbc30033
helpviewer_keywords:
- BC30033
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
ms.openlocfilehash: f2439c4bfc53f906fdc277b0de1faac0941c8808
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796099"
---
# <a name="bc30033-identifier-is-too-long"></a><span data-ttu-id="3580b-103">BC30033: tanımlayıcı çok uzun</span><span class="sxs-lookup"><span data-stu-id="3580b-103">BC30033: Identifier is too long</span></span>

<span data-ttu-id="3580b-104">Her programlama öğesinin adı veya tanımlayıcı 1023 karakterle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="3580b-104">The name, or identifier, of every programming element is limited to 1023 characters.</span></span> <span data-ttu-id="3580b-105">Ayrıca, tam nitelikli ad 1023 karakterden uzun olamaz.</span><span class="sxs-lookup"><span data-stu-id="3580b-105">In addition, a fully qualified name cannot exceed 1023 characters.</span></span> <span data-ttu-id="3580b-106">Bu, tüm tanımlayıcı dizesinin ( `<namespace>.<...>.<namespace>.<class>.<element>` ), üye erişim işleci () karakterleri dahil 1023 karakterden uzun olamayacağı anlamına gelir `.` .</span><span class="sxs-lookup"><span data-stu-id="3580b-106">This means that the entire identifier string (`<namespace>.<...>.<namespace>.<class>.<element>`) cannot be more than 1023 characters long, including the member-access operator (`.`) characters.</span></span>

 <span data-ttu-id="3580b-107">**Hata kimliği:** BC30033</span><span class="sxs-lookup"><span data-stu-id="3580b-107">**Error ID:** BC30033</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3580b-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3580b-108">To correct this error</span></span>

- <span data-ttu-id="3580b-109">Tanımlayıcının uzunluğunu azaltın.</span><span class="sxs-lookup"><span data-stu-id="3580b-109">Reduce the length of the identifier.</span></span>

## <a name="see-also"></a><span data-ttu-id="3580b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3580b-110">See also</span></span>

- [<span data-ttu-id="3580b-111">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="3580b-111">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
