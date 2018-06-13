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
ms.openlocfilehash: 3c1d1944ae06ea26ce9bf7b4726e79155768d444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405307"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)
Yazılım Yayımcı Sertifikası Test aracı, bir veya daha fazla X.509 sertifikasından bir Yazılım Yayımcısı Sertifikası (SPC) oluşturur. Cert2spc.exe, yalnızca test amaçlıdır. VeriSign ya da Thawte gibi bir Sertifika Yetkilisi'nden geçerli bir SPC edinebilirsiniz. X.509 sertifikaları oluşturma hakkında daha fazla bilgi için bkz: [Makecert.exe (sertifika oluşturma aracı)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`certN.cer`|SPC dosyasına eklenecek bir X.509 sertifikasının adı. Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.|  
|`crlN.crl`|SPC dosyasına eklenecek bir sertifika iptal listesinin adı. Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.|  
|`outputSPCfile.spc`|X.509 sertifikaları içeren PKCS #7 nesnesinin adı.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut bir SPC gelen oluşturur `myCertificate.cer` ve yerleştirir `mySPCFile.spc`.  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 Aşağıdaki komut bir SPC gelen oluşturur `oneCertificate.cer` ve `twoCertificate.cer`ve yerleştirir `mySPCFile.spc`.  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [MakeCert.exe (sertifika oluşturma aracı)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
