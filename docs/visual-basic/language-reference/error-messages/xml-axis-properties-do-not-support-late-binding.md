---
title: XML eksen özellikleri geç bağlamayı desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- bc31168
- vbc31168
helpviewer_keywords:
- BC31168
ms.assetid: 45707363-55e4-4151-892d-d8729106355b
ms.openlocfilehash: caa0934ba4ab7e80ae9598b4772e5e49c1ec7f41
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875020"
---
# <a name="xml-axis-properties-do-not-support-late-binding"></a><span data-ttu-id="69b82-102">XML eksen özellikleri geç bağlamayı desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="69b82-102">XML axis properties do not support late binding</span></span>

<span data-ttu-id="69b82-103">Türsüz bir nesne için bir XML ekseni özelliğine başvuruldu.</span><span class="sxs-lookup"><span data-stu-id="69b82-103">An XML axis property has been referenced for an untyped object.</span></span>  
  
 <span data-ttu-id="69b82-104">**Hata kimliği:** BC31168</span><span class="sxs-lookup"><span data-stu-id="69b82-104">**Error ID:** BC31168</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="69b82-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="69b82-105">To correct this error</span></span>  
  
- <span data-ttu-id="69b82-106">XML eksen özelliğine başvurmadan önce nesnenin kesin türü belirtilmiş bir nesne olduğundan emin olun <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="69b82-106">Ensure that the object is a strong-typed <xref:System.Xml.Linq.XElement> object before referencing the XML axis property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b82-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69b82-107">See also</span></span>

- [<span data-ttu-id="69b82-108">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="69b82-108">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="69b82-109">XML</span><span class="sxs-lookup"><span data-stu-id="69b82-109">XML</span></span>](../../programming-guide/language-features/xml/index.md)
