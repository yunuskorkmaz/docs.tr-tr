---
title: Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a18c10df32b9e958147bd132a27a4dba47389cc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044801"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)
Yazılım Yayımcı Sertifikası Test aracı, bir veya daha fazla X.509 sertifikasından bir Yazılım Yayımcısı Sertifikası (SPC) oluşturur. Cert2spc.exe, yalnızca test amaçlıdır. VeriSign ya da Thawte gibi bir Sertifika Yetkilisi'nden geçerli bir SPC edinebilirsiniz. X. 509.952 sertifikaları oluşturma hakkında daha fazla bilgi için bkz. [MakeCert. exe (sertifika oluşturma aracı)](/windows/desktop/SecCrypto/makecert).  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`certN.cer`|SPC dosyasına eklenecek bir X.509 sertifikasının adı. Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.|  
|`crlN.crl`|SPC dosyasına eklenecek bir sertifika iptal listesinin adı. Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.|  
|`outputSPCfile.spc`|X.509 sertifikaları içeren PKCS #7 nesnesinin adı.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, ' dan `myCertificate.cer` bir SPC oluşturur ve bunu içine `mySPCFile.spc`koyar.  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 Aşağıdaki komut, ve `oneCertificate.cer` `twoCertificate.cer`' dan bir SPC oluşturur ve içine `mySPCFile.spc`koyar.  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [MakeCert. exe (sertifika oluşturma aracı)](/windows/desktop/SecCrypto/makecert)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
