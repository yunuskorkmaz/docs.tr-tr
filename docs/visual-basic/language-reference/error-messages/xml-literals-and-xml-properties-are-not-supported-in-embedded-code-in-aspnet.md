---
title: ASP.NET içine katıştırılmış kodda XML sabit değerleri ve XML özellikleri desteklenmez.
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: d96386f8495685391203826fea85efba47c44951
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163265"
---
# <a name="bc31200-xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="b48b5-102">BC31200: ASP.NET içindeki gömülü kodda XML sabit değerleri ve XML özellikleri desteklenmez</span><span class="sxs-lookup"><span data-stu-id="b48b5-102">BC31200: XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>

<span data-ttu-id="b48b5-103">ASP.NET içindeki katıştırılmış kodda XML sabit değerleri ve XML özellikleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b48b5-103">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="b48b5-104">XML özelliklerini kullanmak için kodu arka plan kodu ' na taşıyın.</span><span class="sxs-lookup"><span data-stu-id="b48b5-104">To use XML features, move the code to code-behind.</span></span>

 <span data-ttu-id="b48b5-105">Bir XML sabit değeri veya XML axis özelliği, bir ASP.NET dosyasında katıştırılmış kod () içinde tanımlanır `<%= =>` .</span><span class="sxs-lookup"><span data-stu-id="b48b5-105">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>

 <span data-ttu-id="b48b5-106">**Hata kimliği:** BC31200</span><span class="sxs-lookup"><span data-stu-id="b48b5-106">**Error ID:** BC31200</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b48b5-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b48b5-107">To correct this error</span></span>

- <span data-ttu-id="b48b5-108">XML literal veya XML Axis özelliğini içeren kodu bir ASP.NET arka plan kod dosyasına taşıyın.</span><span class="sxs-lookup"><span data-stu-id="b48b5-108">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>

## <a name="see-also"></a><span data-ttu-id="b48b5-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b48b5-109">See also</span></span>

- [<span data-ttu-id="b48b5-110">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="b48b5-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="b48b5-111">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="b48b5-111">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="b48b5-112">XML</span><span class="sxs-lookup"><span data-stu-id="b48b5-112">XML</span></span>](../../programming-guide/language-features/xml/index.md)
