---
title: 'Nasıl yapılır: Grup bağlantılar için kullanıcı bilgilerini atayın'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ce550d6-8f7c-4ea7-add8-5bc27a7b51be
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 51e000019999056fd707c1fbf4fa1a9b0a8e7bc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395151"
---
# <a name="how-to-assign-user-information-to-group-connections"></a><span data-ttu-id="36b6c-102">Nasıl yapılır: Grup bağlantılar için kullanıcı bilgilerini atayın</span><span class="sxs-lookup"><span data-stu-id="36b6c-102">How to: Assign User Information to Group Connections</span></span>

  
 <span data-ttu-id="36b6c-103">Aşağıdaki örnek, uygulama değişkenlerini ayarlar varsayılarak grup bağlantıları için kullanıcı bilgilerini atamak gösterilmiştir *kullanıcıadı*, *SecurelyStoredPassword*, ve  *Etki alanı* kodu'nun bu bölümünde çağrılmadan önce ve *kullanıcıadı* benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="36b6c-103">The following example demonstrates how to assign user information to group connections, assuming that the application sets the variables *UserName*, *SecurelyStoredPassword*, and *Domain* before this section of code is called and that *UserName* is unique.</span></span>  
  
### <a name="to-assign-user-information-to-a-group-connection"></a><span data-ttu-id="36b6c-104">Grup bağlantı kullanıcı bilgilerini atamak için</span><span class="sxs-lookup"><span data-stu-id="36b6c-104">To assign user information to a group connection</span></span>  
  
1.  <span data-ttu-id="36b6c-105">Bir bağlantı adı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="36b6c-105">Create a connection group name.</span></span>  
  
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
  
2.  <span data-ttu-id="36b6c-106">Belirli bir URL için bir istek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="36b6c-106">Create a request for a specific URL.</span></span> <span data-ttu-id="36b6c-107">Örneğin, aşağıdaki kod bir istek için URL oluşturur `http://www.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="36b6c-107">For example, the following code creates a request for the URL `http://www.contoso.com.`</span></span>  
  
    ```csharp  
    WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
    ```  
  
    ```vb  
    Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ```  
  
3.  <span data-ttu-id="36b6c-108">Web isteği ve arama için kimlik bilgileri ve bağlantı GroupName Ayarla **GetResponse** almak için bir **WebResponse** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="36b6c-108">Set the credentials and Connection GroupName for the Web request, and call **GetResponse** to retrieve a **WebResponse** object.</span></span>  
  
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
  
4.  <span data-ttu-id="36b6c-109">Yanıt akışı WebRespose nesne kullanıldıktan sonra kapatın.</span><span class="sxs-lookup"><span data-stu-id="36b6c-109">Close the response stream after using the WebRespose object.</span></span>  
  
    ```csharp  
    MyWebResponse.Close();  
    ```  
  
    ```vb  
    MyWebResponse.Close()  
    ```  
  
 <span data-ttu-id="36b6c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="36b6c-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36b6c-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36b6c-111">See Also</span></span>  
 [<span data-ttu-id="36b6c-112">Bağlantıları Yönetme</span><span class="sxs-lookup"><span data-stu-id="36b6c-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)  
 [<span data-ttu-id="36b6c-113">Bağlantı Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="36b6c-113">Connection Grouping</span></span>](../../../docs/framework/network-programming/connection-grouping.md)
