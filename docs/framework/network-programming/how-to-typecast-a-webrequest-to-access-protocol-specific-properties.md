---
description: 'Daha fazla bilgi edinin: nasıl yapılır: Web Isteği protokolüne özgü özelliklere erişim için tür dönüştürme'
title: 'Nasıl yapılır: WebRequest Türü Atayarak Protokole Özgü Özelliklere Erişim'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: 24c07a3f2d77dec180476dec3c58f07b40e00c8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662747"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a><span data-ttu-id="04ff5-103">Nasıl yapılır: WebRequest Türü Atayarak Protokole Özgü Özelliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="04ff5-103">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>

<span data-ttu-id="04ff5-104">Bu örnek, protokole özgü özelliklere erişebilmek için bir WebRequest 'in nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="04ff5-104">This example shows how to typecast a WebRequest so that you can access protocol specific properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04ff5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="04ff5-105">Example</span></span>  
  
```csharp  
HttpWebRequest httpreq =
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a><span data-ttu-id="04ff5-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04ff5-106">See also</span></span>

- [<span data-ttu-id="04ff5-107">Takılabilir Protokoller Programlama</span><span class="sxs-lookup"><span data-stu-id="04ff5-107">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
