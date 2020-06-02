---
title: .NET 'te temel dize Işlemleri
description: Dizeler üzerinde gerçekleştirebileceğiniz temel işlemler hakkında bilgi edinin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 8c19f6bcbdf5e4829c91aee1e2fd631537ed2e0a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277758"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="ae9aa-103">.NET 'te temel dize işlemleri</span><span class="sxs-lookup"><span data-stu-id="ae9aa-103">Basic string operations in .NET</span></span>

<span data-ttu-id="ae9aa-104">Uygulamalar genellikle kullanıcı girişine göre iletiler oluşturarak kullanıcılara yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="ae9aa-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="ae9aa-105">Örneğin, Web sitelerinin Kullanıcı adını içeren özelleştirilmiş bir karşılama ile yeni bir oturum açan kullanıcıya yanıt vermesi yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="ae9aa-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="ae9aa-106"><xref:System.String?displayProperty=nameWithType>Ve sınıflardaki çeşitli yöntemler, <xref:System.Text.StringBuilder?displayProperty=nameWithType> Kullanıcı arabiriminizdeki görüntülenecek özel dizeleri dinamik olarak oluşturmanız için izin verir.</span><span class="sxs-lookup"><span data-stu-id="ae9aa-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="ae9aa-107">Bu yöntemler Ayrıca bayt dizelerinden yeni dizeler oluşturma, dizelerin değerlerini karşılaştırma ve mevcut dizeleri değiştirme gibi birçok temel dize işlemi gerçekleştirmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="ae9aa-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="ae9aa-108">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="ae9aa-108">Related sections</span></span>

<span data-ttu-id="ae9aa-109">[.NET 'te tür dönüştürme](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="ae9aa-109">[Type Conversion in .NET](type-conversion.md)</span></span>\
<span data-ttu-id="ae9aa-110">Bir türün başka bir türe nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ae9aa-110">Describes how to convert one type into another type.</span></span>  

<span data-ttu-id="ae9aa-111">[Biçimlendirme türleri](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="ae9aa-111">[Formatting Types](formatting-types.md)</span></span>\
<span data-ttu-id="ae9aa-112">Biçim belirticilerini kullanarak dizelerin nasıl biçimlendirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ae9aa-112">Describes how to format strings using format specifiers.</span></span>
