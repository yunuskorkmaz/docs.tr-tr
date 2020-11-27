---
title: Güvenli Yuva Katmanı Kullanma
description: System.Net ve genişletme sınıflarının, .NET Framework çeşitli ağ protokolleri bağlantısını şifrelemek için Güvenli Yuva Katmanı nasıl kullandığını öğrenin.
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
ms.openlocfilehash: 1309e9dc594869cec7bce81ef666d9f5e06f13b9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265186"
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="0d12c-103">Güvenli Yuva Katmanı Kullanma</span><span class="sxs-lookup"><span data-stu-id="0d12c-103">Using Secure Sockets Layer</span></span>

<span data-ttu-id="0d12c-104"><xref:System.Net>Sınıflar, birkaç ağ protokolünün bağlantısını şifrelemek için Güvenli Yuva Katmanı (SSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d12c-104">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="0d12c-105">Http bağlantılarında, <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları SSL 'yi destekleyen Web Konakları ile iletişim kurmak için SSL kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d12c-105">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="0d12c-106">SSL kullanma kararı, <xref:System.Net.WebRequest> VERILEN URI temel alınarak sınıfı tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="0d12c-106">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="0d12c-107">URI "https:" ile başlıyorsa, SSL kullanılır; URI "http:" ile başlıyorsa, şifrelenmemiş bir bağlantı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d12c-107">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="0d12c-108">SSL 'yi Dosya Aktarım Protokolü (FTP) ile birlikte kullanmak için, <xref:System.Net.FtpWebRequest.EnableSsl> çağrılmadan önce özelliği true olarak ayarlayın <xref:System.Net.FtpWebRequest.GetResponse> .</span><span class="sxs-lookup"><span data-stu-id="0d12c-108">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="0d12c-109">Benzer şekilde, Basit Posta Aktarım Protokolü (SMTP) ile SSL kullanmak için, <xref:System.Net.Mail.SmtpClient.EnableSsl> e-postayı göndermeden önce özelliğini doğru olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0d12c-109">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="0d12c-110"><xref:System.Net.Security.SslStream>Sınıfı, SSL için akış tabanlı bir soyutlama sağlar ve SSL anlaşmasını yapılandırmak için birçok yol sunar.</span><span class="sxs-lookup"><span data-stu-id="0d12c-110">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d12c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d12c-111">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="0d12c-112">Kod</span><span class="sxs-lookup"><span data-stu-id="0d12c-112">Code</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="0d12c-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0d12c-113">Compiling the Code</span></span>  

 <span data-ttu-id="0d12c-114">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0d12c-114">This example requires:</span></span>  
  
- <span data-ttu-id="0d12c-115">**System.net** ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="0d12c-115">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d12c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d12c-116">See also</span></span>

- [<span data-ttu-id="0d12c-117">Ağ Programlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0d12c-117">Security in Network Programming</span></span>](security-in-network-programming.md)
- [<span data-ttu-id="0d12c-118">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="0d12c-118">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="0d12c-119">Sertifika Seçimi ve Doğrulama</span><span class="sxs-lookup"><span data-stu-id="0d12c-119">Certificate Selection and Validation</span></span>](certificate-selection-and-validation.md)
