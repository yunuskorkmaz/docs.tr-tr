---
title: 'Nasıl yapılır: Bağlantıları Gruplandırmak için Kullanıcı Bilgileri Atama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ce550d6-8f7c-4ea7-add8-5bc27a7b51be
ms.openlocfilehash: 01b686702250c68131e8a46b410ce05e67e7c950
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180839"
---
# <a name="how-to-assign-user-information-to-group-connections"></a><span data-ttu-id="70809-102">Nasıl yapılır: Bağlantıları Gruplandırmak için Kullanıcı Bilgileri Atama</span><span class="sxs-lookup"><span data-stu-id="70809-102">How to: Assign User Information to Group Connections</span></span>

 <span data-ttu-id="70809-103">Aşağıdaki örnek, uygulamanın kullanıcı *adı*, *Güvenli StoredPassword*ve *Etki Alanı* değişkenlerini kod bu bölümü aranmadan önce ayarladığını ve *Kullanıcı Adı'nın* benzersiz olduğunu varsayarak, kullanıcı bilgilerinin grup bağlantılarına nasıl atanacağımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="70809-103">The following example demonstrates how to assign user information to group connections, assuming that the application sets the variables *UserName*, *SecurelyStoredPassword*, and *Domain* before this section of code is called and that *UserName* is unique.</span></span>  
  
### <a name="to-assign-user-information-to-a-group-connection"></a><span data-ttu-id="70809-104">Kullanıcı bilgilerini grup bağlantısına atamak için</span><span class="sxs-lookup"><span data-stu-id="70809-104">To assign user information to a group connection</span></span>  
  
1. <span data-ttu-id="70809-105">Bir bağlantı grubu adı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="70809-105">Create a connection group name.</span></span>  
  
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
  
2. <span data-ttu-id="70809-106">Belirli bir URL için istek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="70809-106">Create a request for a specific URL.</span></span> <span data-ttu-id="70809-107">Örneğin, aşağıdaki kod URL için bir istek oluşturur`http://www.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="70809-107">For example, the following code creates a request for the URL `http://www.contoso.com.`</span></span>  
  
    ```csharp  
    WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
    ```  
  
    ```vb  
    Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ```  
  
3. <span data-ttu-id="70809-108">Web isteği için kimlik bilgilerini ve Bağlantı Grubu Adını ayarlayın ve **Bir WebYanıt** nesnesini almak için **GetResponse'u** arayın.</span><span class="sxs-lookup"><span data-stu-id="70809-108">Set the credentials and Connection GroupName for the Web request, and call **GetResponse** to retrieve a **WebResponse** object.</span></span>  
  
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
  
4. <span data-ttu-id="70809-109">WebRespose nesnesini kullandıktan sonra yanıt akışını kapatın.</span><span class="sxs-lookup"><span data-stu-id="70809-109">Close the response stream after using the WebRespose object.</span></span>  
  
    ```csharp  
    MyWebResponse.Close();  
    ```  
  
    ```vb  
    MyWebResponse.Close()  
    ```  
  
 <span data-ttu-id="70809-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="70809-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70809-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70809-111">See also</span></span>

- [<span data-ttu-id="70809-112">Bağlantıları Yönetme</span><span class="sxs-lookup"><span data-stu-id="70809-112">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="70809-113">Bağlantı Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="70809-113">Connection Grouping</span></span>](connection-grouping.md)
