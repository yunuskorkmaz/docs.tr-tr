---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Kullanıcı bilgilerini grup bağlantılarına atama'
title: 'Nasıl yapılır: Bağlantıları Gruplandırmak için Kullanıcı Bilgileri Atama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ce550d6-8f7c-4ea7-add8-5bc27a7b51be
ms.openlocfilehash: 2af901b91c561f5f46c63ed627cbd0053d30e624
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729269"
---
# <a name="how-to-assign-user-information-to-group-connections"></a><span data-ttu-id="66dd4-103">Nasıl yapılır: Bağlantıları Gruplandırmak için Kullanıcı Bilgileri Atama</span><span class="sxs-lookup"><span data-stu-id="66dd4-103">How to: Assign User Information to Group Connections</span></span>

 <span data-ttu-id="66dd4-104">Aşağıdaki örnek, bu kodun bu bölümü çağrılmadan ve *Kullanıcı adının* benzersiz olması Için uygulamanın *UserName*, *securelyStoredPassword* ve *Domain* değişkenlerini ayarladığını varsayarak, Kullanıcı bilgilerinin grup bağlantılarına nasıl atanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="66dd4-104">The following example demonstrates how to assign user information to group connections, assuming that the application sets the variables *UserName*, *SecurelyStoredPassword*, and *Domain* before this section of code is called and that *UserName* is unique.</span></span>  
  
### <a name="to-assign-user-information-to-a-group-connection"></a><span data-ttu-id="66dd4-105">Kullanıcı bilgilerini bir grup bağlantısına atamak için</span><span class="sxs-lookup"><span data-stu-id="66dd4-105">To assign user information to a group connection</span></span>  
  
1. <span data-ttu-id="66dd4-106">Bir bağlantı grubu adı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="66dd4-106">Create a connection group name.</span></span>  
  
    ```csharp  
    SHA1Managed Sha1 = new SHA1Managed();  
    Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
    String secureGroupName = Encoding.Default.GetString(updHash);  
    ```  
  
    ```vb  
    Dim Sha1 As New SHA1Managed()  
    Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
    Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
    ```  
  
2. <span data-ttu-id="66dd4-107">Belirli bir URL için bir istek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="66dd4-107">Create a request for a specific URL.</span></span> <span data-ttu-id="66dd4-108">Örneğin, aşağıdaki kod URL için bir istek oluşturur `http://www.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="66dd4-108">For example, the following code creates a request for the URL `http://www.contoso.com.`</span></span>  
  
    ```csharp  
    WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
    ```  
  
    ```vb  
    Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ```  
  
3. <span data-ttu-id="66dd4-109">Web isteği için kimlik bilgilerini ve bağlantı grubuadı ' nı ayarlayın ve bir **WebResponse** nesnesi almak Için **GetResponse** öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="66dd4-109">Set the credentials and Connection GroupName for the Web request, and call **GetResponse** to retrieve a **WebResponse** object.</span></span>  
  
    ```csharp  
    myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);
    myWebRequest.ConnectionGroupName = secureGroupName;  
  
    WebResponse myWebResponse=myWebRequest.GetResponse();  
    ```  
  
    ```vb  
    myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
    myWebRequest.ConnectionGroupName = secureGroupName  
  
    Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
    ```  
  
4. <span data-ttu-id="66dd4-110">Webrespoz nesnesini kullandıktan sonra yanıt akışını kapatın.</span><span class="sxs-lookup"><span data-stu-id="66dd4-110">Close the response stream after using the WebRespose object.</span></span>  
  
    ```csharp  
    MyWebResponse.Close();  
    ```  
  
    ```vb  
    MyWebResponse.Close()  
    ```  
  
 <span data-ttu-id="66dd4-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="66dd4-111">Example</span></span>  
  
```csharp  
// Create a connection group name.  
SHA1Managed Sha1 = new SHA1Managed();  
Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
String secureGroupName = Encoding.Default.GetString(updHash);  
  
// Create a request for a specific URL.  
WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
  
myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);
myWebRequest.ConnectionGroupName = secureGroupName;  
  
WebResponse myWebResponse=myWebRequest.GetResponse();  
  
// Insert the code that uses myWebResponse.  
  
MyWebResponse.Close();  
```  
  
```vb  
' Create a secure group name.  
Dim Sha1 As New SHA1Managed()  
Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
  
' Create a request for a specific URL.  
Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
  
myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
myWebRequest.ConnectionGroupName = secureGroupName  
  
Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
  
' Insert the code that uses myWebResponse.  
MyWebResponse.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="66dd4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66dd4-112">See also</span></span>

- [<span data-ttu-id="66dd4-113">Bağlantıları Yönetme</span><span class="sxs-lookup"><span data-stu-id="66dd4-113">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="66dd4-114">Bağlantı Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="66dd4-114">Connection Grouping</span></span>](connection-grouping.md)
