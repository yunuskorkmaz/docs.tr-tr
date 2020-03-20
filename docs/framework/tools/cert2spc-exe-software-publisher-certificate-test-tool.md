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
ms.openlocfilehash: 809b7d0383f172a5fbcb2ac4ac3ffb96ff0b8e20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129880"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)
Yazılım Yayımcı Sertifikası Test aracı, bir veya daha fazla X.509 sertifikasından bir Yazılım Yayımcısı Sertifikası (SPC) oluşturur. Cert2spc.exe, yalnızca test amaçlıdır. VeriSign ya da Thawte gibi bir Sertifika Yetkilisi'nden geçerli bir SPC edinebilirsiniz. X.509 sertifikaları oluşturma hakkında daha fazla bilgi için [Makecert.exe (Sertifika Oluşturma Aracı)](/windows/desktop/SecCrypto/makecert)bakın.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
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
 Aşağıdaki komut bir `myCertificate.cer` SPC oluşturur ve `mySPCFile.spc`.'ye yerleştirir.  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 Aşağıdaki komut bir SPC `oneCertificate.cer` oluşturur `twoCertificate.cer`ve , `mySPCFile.spc`ve yerleştirir.  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Makecert.exe (Sertifika Oluşturma Aracı)](/windows/desktop/SecCrypto/makecert)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
