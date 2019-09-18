---
title: İnternet İstekleri Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 80e3a6bd199691df9391e88d5a64fab5df2a08a1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048614"
---
# <a name="creating-internet-requests"></a>İnternet İstekleri Oluşturma
Uygulamalar, <xref:System.Net.WebRequest> <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntemi aracılığıyla örnek oluşturur. Bu, kendisine geçirilen URI şemasını temel alan **WebRequest** 'ten türetilmiş bir sınıf oluşturan statik bir yöntemdir.  
  
## <a name="web-file-and-ftp-requests"></a>Web, dosya ve FTP Istekleri  
 .NET Framework, http ve <xref:System.Net.HttpWebRequest> https isteklerini işlemek için **WebRequest**'ten türetilen sınıfı sağlar. Çoğu durumda, **WebRequest** sınıfı bir istek yapmak için ihtiyacınız olan tüm özellikleri sağlar; Ancak, gerekirse, isteğin HTTP 'e özgü özelliklerine erişmek için **Web isteği. Create** yöntemi tarafından oluşturulan **WebRequest** nesnelerini **HttpWebRequest** türüne çevirebilirsiniz. Benzer şekilde, **HttpWebResponse** nesnesi http ve https isteklerindeki yanıtları işler. **HttpWebResponse** nesnesinin http 'e özgü özelliklerine erişmek Için **WebResponse** nesnelerini **HttpWebResponse** türüne atamalısınız.  
  
 .NET Framework Ayrıca, "dosya <xref:System.Net.FileWebRequest> : <xref:System.Net.FileWebResponse> " kullanan kaynaklara yönelik istekleri işlemek için ve sınıflarını sağlar. URI şeması. Benzer şekilde, <xref:System.Net.FtpWebResponse>vesınıfları "FTP:" düzenini kullanan kaynaklar için istekleri işlemek üzere sağlanır. <xref:System.Net.FtpWebRequest> İsteğiniz bu düzenlerden herhangi birini kullanan bir kaynak için ise, isteğinizi yapmak için bir nesne elde etmek üzere **WebRequest. Create** yöntemini kullanabilirsiniz.  
  
 Diğer uygulama düzeyi protokolleri kullanan istekleri işlemek için **WebRequest** ve **WebResponse**'dan türetilmiş protokole özgü sınıfları uygulamanız gerekir. Daha fazla bilgi için bkz. [takılabilir protokolleri programlama](programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme](how-to-request-data-using-the-webrequest-class.md)
- [Veri İsteme](requesting-data.md)
