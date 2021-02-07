---
description: 'Hakkında daha fazla bilgi edinin: BC31200: XML sabit değerleri ve XML özellikleri ASP.NET içindeki gömülü kodda desteklenmez'
title: ASP.NET içine katıştırılmış kodda XML sabit değerleri ve XML özellikleri desteklenmez.
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 0a5328676ee38a56334b77f665a464daa586ce3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701410"
---
# <a name="bc31200-xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="fd488-103">BC31200: ASP.NET içindeki gömülü kodda XML sabit değerleri ve XML özellikleri desteklenmez</span><span class="sxs-lookup"><span data-stu-id="fd488-103">BC31200: XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>

<span data-ttu-id="fd488-104">ASP.NET içindeki katıştırılmış kodda XML sabit değerleri ve XML özellikleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="fd488-104">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="fd488-105">XML özelliklerini kullanmak için kodu arka plan kodu ' na taşıyın.</span><span class="sxs-lookup"><span data-stu-id="fd488-105">To use XML features, move the code to code-behind.</span></span>

 <span data-ttu-id="fd488-106">Bir XML sabit değeri veya XML axis özelliği, bir ASP.NET dosyasında katıştırılmış kod () içinde tanımlanır `<%= =>` .</span><span class="sxs-lookup"><span data-stu-id="fd488-106">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>

 <span data-ttu-id="fd488-107">**Hata kimliği:** BC31200</span><span class="sxs-lookup"><span data-stu-id="fd488-107">**Error ID:** BC31200</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fd488-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fd488-108">To correct this error</span></span>

- <span data-ttu-id="fd488-109">XML literal veya XML Axis özelliğini içeren kodu bir ASP.NET arka plan kod dosyasına taşıyın.</span><span class="sxs-lookup"><span data-stu-id="fd488-109">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd488-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd488-110">See also</span></span>

- [<span data-ttu-id="fd488-111">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="fd488-111">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="fd488-112">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="fd488-112">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="fd488-113">XML</span><span class="sxs-lookup"><span data-stu-id="fd488-113">XML</span></span>](../../programming-guide/language-features/xml/index.md)
