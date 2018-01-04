---
title: "Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5a8363b0ec059c1ae94b7ab53e5c3064a06541f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
