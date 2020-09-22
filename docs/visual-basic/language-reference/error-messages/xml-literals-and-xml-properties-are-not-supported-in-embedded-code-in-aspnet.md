---
title: ASP.NET içine katıştırılmış kodda XML sabit değerleri ve XML özellikleri desteklenmez.
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 861677636f9a73015b26efec30df728d07fbdf72
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870212"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="a1d46-102">ASP.NET içine katıştırılmış kodda XML sabit değerleri ve XML özellikleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a1d46-102">XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>

<span data-ttu-id="a1d46-103">ASP.NET içindeki katıştırılmış kodda XML sabit değerleri ve XML özellikleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a1d46-103">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="a1d46-104">XML özelliklerini kullanmak için kodu arka plan kodu ' na taşıyın.</span><span class="sxs-lookup"><span data-stu-id="a1d46-104">To use XML features, move the code to code-behind.</span></span>  
  
 <span data-ttu-id="a1d46-105">Bir XML sabit değeri veya XML axis özelliği, bir ASP.NET dosyasında katıştırılmış kod () içinde tanımlanır `<%= =>` .</span><span class="sxs-lookup"><span data-stu-id="a1d46-105">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>  
  
 <span data-ttu-id="a1d46-106">**Hata kimliği:** BC31200</span><span class="sxs-lookup"><span data-stu-id="a1d46-106">**Error ID:** BC31200</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a1d46-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a1d46-107">To correct this error</span></span>  
  
- <span data-ttu-id="a1d46-108">XML literal veya XML Axis özelliğini içeren kodu bir ASP.NET arka plan kod dosyasına taşıyın.</span><span class="sxs-lookup"><span data-stu-id="a1d46-108">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d46-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1d46-109">See also</span></span>

- [<span data-ttu-id="a1d46-110">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="a1d46-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="a1d46-111">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="a1d46-111">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="a1d46-112">XML</span><span class="sxs-lookup"><span data-stu-id="a1d46-112">XML</span></span>](../../programming-guide/language-features/xml/index.md)
