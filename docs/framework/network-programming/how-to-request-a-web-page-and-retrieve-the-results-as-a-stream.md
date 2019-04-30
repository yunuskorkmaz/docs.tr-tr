---
title: 'Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 23c094f0a3f528750c9589dbc99a0ada86236967
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642548"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="4cb78-102">Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma</span><span class="sxs-lookup"><span data-stu-id="4cb78-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="4cb78-103">Bu örnek, bir Web sayfası isteme ve sonuçları bir akış alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4cb78-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cb78-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4cb78-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="4cb78-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4cb78-105">Compiling the Code</span></span>  
 <span data-ttu-id="4cb78-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="4cb78-106">This example requires:</span></span>  
  
- <span data-ttu-id="4cb78-107">Başvurular <xref:System.IO> ve <xref:System.Net> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="4cb78-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb78-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cb78-108">See also</span></span>

- [<span data-ttu-id="4cb78-109">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="4cb78-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
