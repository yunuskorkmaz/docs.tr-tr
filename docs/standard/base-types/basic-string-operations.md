---
title: .NET 'te temel dize Işlemleri
description: Dizeler üzerinde gerçekleştirebileceğiniz temel işlemler hakkında bilgi edinin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 4ab087435880c6a5357bc161899cd585982622f4
ms.sourcegitcommit: ffd4d5e824db6c5f0c3521c0e802fd9e8f0edcbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93342611"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="c9e83-103">.NET 'te temel dize işlemleri</span><span class="sxs-lookup"><span data-stu-id="c9e83-103">Basic string operations in .NET</span></span>

<span data-ttu-id="c9e83-104">Uygulamalar genellikle kullanıcı girişine göre iletiler oluşturarak kullanıcılara yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="c9e83-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="c9e83-105">Örneğin, Web sitelerinin Kullanıcı adını içeren özelleştirilmiş bir karşılama ile yeni bir oturum açan kullanıcıya yanıt vermesi yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="c9e83-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="c9e83-106"><xref:System.String?displayProperty=nameWithType>Ve sınıflardaki çeşitli yöntemler, <xref:System.Text.StringBuilder?displayProperty=nameWithType> Kullanıcı arabiriminizdeki görüntülenecek özel dizeleri dinamik olarak oluşturmanız için izin verir.</span><span class="sxs-lookup"><span data-stu-id="c9e83-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="c9e83-107">Bu yöntemler Ayrıca bayt dizelerinden yeni dizeler oluşturma, dizelerin değerlerini karşılaştırma ve mevcut dizeleri değiştirme gibi birçok temel dize işlemi gerçekleştirmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c9e83-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c9e83-108">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="c9e83-108">Related sections</span></span>

<span data-ttu-id="c9e83-109">[.NET 'te tür dönüştürme](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="c9e83-109">[Type Conversion in .NET](type-conversion.md)</span></span>\
<span data-ttu-id="c9e83-110">Bir türün başka bir türe nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c9e83-110">Describes how to convert one type into another type.</span></span>

<span data-ttu-id="c9e83-111">[Biçimlendirme türleri](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="c9e83-111">[Formatting Types](formatting-types.md)</span></span>\
<span data-ttu-id="c9e83-112">Biçim belirticilerini kullanarak dizelerin nasıl biçimlendirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c9e83-112">Describes how to format strings using format specifiers.</span></span>
