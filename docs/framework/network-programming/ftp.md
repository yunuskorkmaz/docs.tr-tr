---
title: FTP-.NET
description: .NET Framework FTP protokolü için, FtpWebRequest ve FtpWebResponse sınıflarını kullanarak sağladığı kapsamlı destek hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d21ca43cd1041df358dc5e2add9560fb33e85d83
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502593"
---
# <a name="ftp"></a>FTP

.NET Framework, ve sınıflarıyla FTP protokolü için kapsamlı destek sağlar <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> . Bu sınıflar <xref:System.Net.WebRequest> ve ' den türetilir <xref:System.Net.WebResponse> . Çoğu durumda, <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları isteği yapmak için gereken tüm öğeleri sağlar, ancak özellik olarak sunulan FTP 'ye özgü özelliklere erişmeniz gerekiyorsa, bu sınıfları veya olarak yazabilirsiniz <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> .

## <a name="examples"></a>Örnekler

Daha fazla bilgi için şu konulara bakın: [nasıl yapılır: FTP Ile dosya indirme](how-to-download-files-with-ftp.md), [nasıl yapılır: FTP ile dosya](how-to-upload-files-with-ftp.md)yükleme ve [nasıl yapılır: FTP ile dizin içeriğini listeleme](how-to-list-directory-contents-with-ftp.md).

## <a name="ftp-and-proxies"></a>FTP ve proxy 'ler

Bir ara sunucu (özelliği ile belirtilen <xref:System.Net.FtpWebRequest.Proxy%2A> ) BIR http proxy 'si ise, yalnızca, <xref:System.Net.WebRequestMethods.Ftp.DownloadFile> <xref:System.Net.WebRequestMethods.Ftp.ListDirectory> ve <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> komutları desteklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Ara Sunucu Üzerinden İnternet Erişimi](accessing-the-internet-through-a-proxy.md)
- [Ağ Programlama Örnekleri](network-programming-samples.md)
- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
