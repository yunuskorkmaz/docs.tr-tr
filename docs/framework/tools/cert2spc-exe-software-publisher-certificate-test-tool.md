---
title: Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)
description: Yazılım yayımcısı sertifika test aracı Cert2spc.exe kullanın. Bu araç bir veya daha fazla X. 509.440 sertifikasından bir yazılım yayımcısı sertifikası (SPC) oluşturur.
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: d2bd0fdc07b87a9b21b281669a213a048a407595
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654212"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)

Yazılım Yayımcı Sertifikası Test aracı, bir veya daha fazla X.509 sertifikasından bir Yazılım Yayımcısı Sertifikası (SPC) oluşturur. Cert2spc.exe, yalnızca test amaçlıdır. VeriSign ya da Thawte gibi bir Sertifika Yetkilisi'nden geçerli bir SPC edinebilirsiniz. X. 509.440 sertifikaları oluşturma hakkında daha fazla bilgi için bkz. [Makecert.exe (sertifika oluşturma aracı)](/windows/desktop/SecCrypto/makecert).  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)kullanın.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Description|  
|--------------|-----------------|  
|`certN.cer`|SPC dosyasına eklenecek bir X.509 sertifikasının adı. Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.|  
|`crlN.crl`|SPC dosyasına eklenecek bir sertifika iptal listesinin adı. Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.|  
|`outputSPCfile.spc`|X.509 sertifikaları içeren PKCS #7 nesnesinin adı.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="examples"></a>Örnekler  

 Aşağıdaki komut, ' dan bir SPC oluşturur `myCertificate.cer` ve bunu içine koyar `mySPCFile.spc` .  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 Aşağıdaki komut, ve ' dan bir SPC oluşturur `oneCertificate.cer` `twoCertificate.cer` ve içine koyar `mySPCFile.spc` .  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Makecert.exe (sertifika oluşturma aracı)](/windows/desktop/SecCrypto/makecert)
- [Geliştirici komut satırı kabukları](/visualstudio/ide/reference/command-prompt-powershell)
