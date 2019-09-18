---
title: Güvenli Yuva Katmanı Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Networking
- SSL
- Secure Sockets Layer
- requesting data from Internet, Secure Sockets Layer
- sending data, Secure Sockets Layer
- Network Resources
- data requests, Secure Sockets Layer
- receiving data, Secure Sockets Layer
- Internet, Secure Sockets Layer
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
ms.openlocfilehash: ef2abc7574aea1b4f77ff93545ad84678c66ce48
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046898"
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="8aaac-102">Güvenli Yuva Katmanı Kullanma</span><span class="sxs-lookup"><span data-stu-id="8aaac-102">Using Secure Sockets Layer</span></span>
<span data-ttu-id="8aaac-103"><xref:System.Net> Sınıflar, birkaç ağ protokolünün bağlantısını şifrelemek için Güvenli Yuva Katmanı (SSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="8aaac-103">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="8aaac-104">Http bağlantılarında <xref:System.Net.WebRequest> , ve <xref:System.Net.WebResponse> sınıfları SSL 'yi destekleyen Web Konakları ile iletişim kurmak için SSL kullanır.</span><span class="sxs-lookup"><span data-stu-id="8aaac-104">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="8aaac-105">SSL kullanma kararı, verilen URI temel alınarak <xref:System.Net.WebRequest> sınıfı tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="8aaac-105">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="8aaac-106">URI "https:" ile başlıyorsa, SSL kullanılır; URI "http:" ile başlıyorsa, şifrelenmemiş bir bağlantı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8aaac-106">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="8aaac-107">SSL 'yi Dosya Aktarım Protokolü (FTP) ile birlikte kullanmak için, <xref:System.Net.FtpWebRequest.EnableSsl> çağrılmadan <xref:System.Net.FtpWebRequest.GetResponse>önce özelliği true olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8aaac-107">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="8aaac-108">Benzer şekilde, Basit Posta Aktarım Protokolü (SMTP) ile SSL kullanmak için, e <xref:System.Net.Mail.SmtpClient.EnableSsl> -postayı göndermeden önce özelliğini doğru olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8aaac-108">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="8aaac-109"><xref:System.Net.Security.SslStream> Sınıfı, SSL için akış tabanlı bir soyutlama sağlar ve SSL anlaşmasını yapılandırmak için birçok yol sunar.</span><span class="sxs-lookup"><span data-stu-id="8aaac-109">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8aaac-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="8aaac-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="8aaac-111">Kod</span><span class="sxs-lookup"><span data-stu-id="8aaac-111">Code</span></span>  
  
```vb  
Dim MyURI As String = "https://www.contoso.com/"  
Dim Wreq As WebRequest = WebRequest.Create(MyURI)  
  
Dim serverUri As String = "ftp://ftp.contoso.com/file.txt"  
Dim request As FtpWebRequest = CType(WebRequest.Create(serverUri), FtpWebRequest)  
request.Method = WebRequestMethods.Ftp.DeleteFile  
request.EnableSsl = True  
Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)  
```  
  
```csharp  
String MyURI = "https://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
  
String serverUri = "ftp://ftp.contoso.com/file.txt"  
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
request.EnableSsl = true;  
request.Method = WebRequestMethods.Ftp.DeleteFile;  
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8aaac-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8aaac-112">Compiling the Code</span></span>  
 <span data-ttu-id="8aaac-113">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8aaac-113">This example requires:</span></span>  
  
- <span data-ttu-id="8aaac-114">**System.net** ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="8aaac-114">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aaac-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8aaac-115">See also</span></span>

- [<span data-ttu-id="8aaac-116">Ağ Programlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8aaac-116">Security in Network Programming</span></span>](security-in-network-programming.md)
- [<span data-ttu-id="8aaac-117">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="8aaac-117">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="8aaac-118">Sertifika Seçimi ve Doğrulama</span><span class="sxs-lookup"><span data-stu-id="8aaac-118">Certificate Selection and Validation</span></span>](certificate-selection-and-validation.md)
