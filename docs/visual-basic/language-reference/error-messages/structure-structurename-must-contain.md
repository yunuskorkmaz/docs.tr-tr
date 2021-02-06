---
description: "Hakkında daha fazla bilgi edinin: BC30941: Structure ' <structurename> ' en az bir örnek üye değişkeni veya en az bir örnek olay bildirimi içermelidir ' Custom"
title: "'<structurename>' yapısı en az bir örnek üye değişkeni veya 'Custom' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir"
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 08596997decd9d739ac95ad3e4191cb126b3efb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641453"
---
# <a name="bc30941-structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="ba330-103">BC30941: ' ' yapısı en \<structurename> az bir örnek üye değişkeni veya ' Custom ' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir</span><span class="sxs-lookup"><span data-stu-id="ba330-103">BC30941: Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>

<span data-ttu-id="ba330-104">Bir yapı tanımı, paylaşılmayan olmayan değişkenler veya paylaşılmayan özel olmayan olaylar içermez.</span><span class="sxs-lookup"><span data-stu-id="ba330-104">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>

 <span data-ttu-id="ba330-105">Her yapının, tek tek ([paylaşılan](../modifiers/shared.md)) tüm örnekler yerine her belirli örnek (paylaşılmayan) için geçerli olan bir değişkene veya olaya sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba330-105">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../modifiers/shared.md)).</span></span> <span data-ttu-id="ba330-106">Paylaşılmayan sabitler, Özellikler ve yordamlar bu gereksinimi karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="ba330-106">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="ba330-107">Ayrıca, paylaşılmayan değişkenler ve yalnızca paylaşılan olmayan bir olay yoksa, bu olay bir `Custom` olay olamaz.</span><span class="sxs-lookup"><span data-stu-id="ba330-107">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>

 <span data-ttu-id="ba330-108">**Hata kimliği:** BC30941</span><span class="sxs-lookup"><span data-stu-id="ba330-108">**Error ID:** BC30941</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ba330-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ba330-109">To correct this error</span></span>

- <span data-ttu-id="ba330-110">En az bir değişken veya olmayan olay tanımlayın `Shared` .</span><span class="sxs-lookup"><span data-stu-id="ba330-110">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="ba330-111">Yalnızca bir olay tanımlarsanız, özel olmayan ve paylaşılmayan olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba330-111">If you define only one event, it must be noncustom as well as nonshared.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba330-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba330-112">See also</span></span>

- [<span data-ttu-id="ba330-113">Yapılar</span><span class="sxs-lookup"><span data-stu-id="ba330-113">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="ba330-114">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="ba330-114">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="ba330-115">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="ba330-115">Structure Statement</span></span>](../statements/structure-statement.md)
