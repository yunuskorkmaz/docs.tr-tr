---
title: .NET'te Temel Dize İşlemleri
description: Dizelerüzerinde gerçekleştirebileceğiniz temel işlemler hakkında bilgi edinin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 2ce1b148a2b1605b5b1283bdc3398409661f3f83
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523984"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="4d426-103">.NET'teki temel dize işlemleri</span><span class="sxs-lookup"><span data-stu-id="4d426-103">Basic string operations in .NET</span></span>

<span data-ttu-id="4d426-104">Uygulamalar genellikle kullanıcı girişine dayalı iletiler oluşturarak kullanıcılara yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="4d426-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="4d426-105">Örneğin, web sitelerinin yeni oturum açmış bir kullanıcıya kullanıcının adını içeren özel bir karşılamayla yanıt vermesi sık rastlanan bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="4d426-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="4d426-106"><xref:System.String?displayProperty=nameWithType> Ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıflardaki çeşitli yöntemler, kullanıcı arabiriminizde görüntülenecek özel dizeleri dinamik olarak oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4d426-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="4d426-107">Bu yöntemler, bayt dizilerinden yeni dizeler oluşturma, dizelerin değerlerini karşılaştırma ve varolan dizeleri değiştirme gibi bir dizi temel dize işlemi gerçekleştirmenize de yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="4d426-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="4d426-108">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="4d426-108">Related sections</span></span>

<span data-ttu-id="4d426-109">[.NET'te Tür Dönüştürme](../../../docs/standard/base-types/type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="4d426-109">[Type Conversion in .NET](../../../docs/standard/base-types/type-conversion.md)</span></span>\
<span data-ttu-id="4d426-110">Bir türü başka bir türe dönüştürme yi açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d426-110">Describes how to convert one type into another type.</span></span>  

<span data-ttu-id="4d426-111">[Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="4d426-111">[Formatting Types](../../../docs/standard/base-types/formatting-types.md)</span></span>\
<span data-ttu-id="4d426-112">Biçim belirteçlerini kullanarak dizeleri nasıl biçimlendireceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d426-112">Describes how to format strings using format specifiers.</span></span>
