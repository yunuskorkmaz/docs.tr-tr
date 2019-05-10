---
title: 'Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 74cb739d381c0b1422d9277be8c3c338a46f8fba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647415"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="e5a09-102">Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma</span><span class="sxs-lookup"><span data-stu-id="e5a09-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="e5a09-103">Bu örnek, bir Web sayfası isteme ve sonuçları bir akış alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5a09-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5a09-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5a09-104">Example</span></span>  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e5a09-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e5a09-105">Compiling the Code</span></span>  
 <span data-ttu-id="e5a09-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e5a09-106">This example requires:</span></span>  
  
- <span data-ttu-id="e5a09-107">Başvurular <xref:System.IO> ve <xref:System.Net> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="e5a09-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a09-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5a09-108">See also</span></span>

- [<span data-ttu-id="e5a09-109">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="e5a09-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
