---
title: "Kullanarak Güvenli Yuva Katmanı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 31c8a3d22e6a7fa074eae18de8f9b2a9903457c1
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="0c166-102">Kullanarak Güvenli Yuva Katmanı</span><span class="sxs-lookup"><span data-stu-id="0c166-102">Using Secure Sockets Layer</span></span>
<span data-ttu-id="0c166-103"><xref:System.Net> Sınıfları birkaç protokolleri ağ için bağlantıyı şifrelemek için Güvenli Yuva Katmanı (SSL) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c166-103">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="0c166-104">Http bağlantıları için <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıflarını SSL desteği web ana bilgisayarlar ile iletişim kurmak için SSL kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c166-104">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="0c166-105">SSL kullanmak üzere kararı tarafından yapılan <xref:System.Net.WebRequest> , verilen URI temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="0c166-105">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="0c166-106">URI ile başlıyorsa "https:", SSL kullanılır; URI ile başlıyorsa "http:", şifrelenmemiş bir bağlantı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c166-106">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="0c166-107">Dosya Aktarım Protokolü (FTP) ile SSL kullanmak üzere ayarlanmış <xref:System.Net.FtpWebRequest.EnableSsl> özelliğinin true çağrılmadan önce <xref:System.Net.FtpWebRequest.GetResponse>.</span><span class="sxs-lookup"><span data-stu-id="0c166-107">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="0c166-108">Benzer şekilde, Basit Posta Aktarım Protokolü (SMTP) ile SSL kullanmak üzere ayarlanmış <xref:System.Net.Mail.SmtpClient.EnableSsl> özelliğinin e-postayı göndermeden önce true.</span><span class="sxs-lookup"><span data-stu-id="0c166-108">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="0c166-109"><xref:System.Net.Security.SslStream> Sınıfı için SSL akışı tabanlı bir Özet sağlar ve SSL el sıkışması yapılandırmak için birçok yol sunar.</span><span class="sxs-lookup"><span data-stu-id="0c166-109">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c166-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c166-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="0c166-111">Kod</span><span class="sxs-lookup"><span data-stu-id="0c166-111">Code</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="0c166-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0c166-112">Compiling the Code</span></span>  
 <span data-ttu-id="0c166-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0c166-113">This example requires:</span></span>  
  
-   <span data-ttu-id="0c166-114">Başvurular **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="0c166-114">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c166-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0c166-115">See Also</span></span>  
 [<span data-ttu-id="0c166-116">Ağ Programlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0c166-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [<span data-ttu-id="0c166-117">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="0c166-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="0c166-118">Sertifika Seçimi ve Doğrulama</span><span class="sxs-lookup"><span data-stu-id="0c166-118">Certificate Selection and Validation</span></span>](../../../docs/framework/network-programming/certificate-selection-and-validation.md)
