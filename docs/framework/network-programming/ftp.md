---
title: FTP - .NET
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d945f03077a863d9e1baa6b59fe8a908566aba5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642886"
---
# <a name="ftp"></a>FTP

.NET Framework, FTP protokolü için <xref:System.Net.FtpWebRequest> sınıflarla <xref:System.Net.FtpWebResponse> kapsamlı bir destek sağlar. Bu sınıflar türetilmiştir <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>. Çoğu durumda, <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıflar istekte bulunmak için gerekli olan her şeyi sağlar, ancak özellik olarak açıkta ftp'ye <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse>özgü özelliklere erişmeniz gerekiyorsa, bu sınıfları veya .

## <a name="examples"></a>Örnekler

Daha fazla bilgi için aşağıdaki konulara bakın: [FTP ile Dosyaları Nasıl İndirin,](how-to-download-files-with-ftp.md) [Nasıl İndirilir: FTP ile Dosya Yükleme](how-to-upload-files-with-ftp.md), ve [Nasıl: FTP ile Dizin İçerikleri Listele](how-to-list-directory-contents-with-ftp.md).

## <a name="ftp-and-proxies"></a>FTP ve vekiller

<xref:System.Net.FtpWebRequest.Proxy%2A> Bir proxy (özellik tarafından belirtilen) bir HTTP proxy <xref:System.Net.WebRequestMethods.Ftp.DownloadFile> <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>ise, <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> o zaman sadece , ve komutları desteklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Ara Sunucu Üzerinden İnternet Erişimi](accessing-the-internet-through-a-proxy.md)
- [Ağ Programlama Örnekleri](network-programming-samples.md)
- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
