---
title: "CorFlags.exe (CorFlags Dönüştürme Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 111c697d4d62cd52cd7913039e3c17e8a25ab50d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (CorFlags Dönüştürme Aracı)
CorFlags Dönüştürme aracı, taşınabilir çalıştırılabilir bir görüntünün üstbilgisinin CorFlags bölümünü yapılandırmanıza olanak verir.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
CorFlags.exe assembly [options]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Gerekli parametre|Açıklama|  
|------------------------|-----------------|  
|`assembly`|CorFlags'in yapılandırılacağı derlemenin adı.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ 32 BIT [REQ] +**|32BITREQUIRED bayrağını ayarlar.|  
|**/ 32 BIT [REQ]-**|32BITREQUIRED bayrağını kaldırır.|  
|**/32BITPREF+**|32BITPREFERRED bayrağını ayarlar. Uygulama 64-bit platformlarda dahi 32-bit işlem olarak çalışır. Bu bayrağı yalnızca EXE dosyalarında ayarlayın. DLL üzerinde bayrağı ayarlarsanız, DLL 64-bit işlemde yüklenemiyordur ve <xref:System.BadImageFormatException> özel durumu oluşur. Bu bayrağı içeren bir EXE dosyası bir 64-bit işleme yüklenebilir.<br /><br /> Yeni [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|**/32BITPREF-**|32BITPREFERRED bayrağını kaldırır.<br /><br /> Yeni [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/ Force**|Derleme bir tanımlayıcı adla adlandırılmış olsa da bir güncelleştirmenin yapılmasını sağlar. **Önemli:** tanımlayıcı adlı bir derleme güncelleştirirseniz, kodu yeniden çalıştırmadan önce imzalamanız gerekir.|  
|**/ Help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/ILONLY+**|ILONLY bayrağını ayarlar.|  
|**/ILONLY-**|ILONLY bayrağını kaldırır.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/ RevertCLRHeader**|CLR üstbilgisini 2.0 sürümüne döndürür.|  
|**/ UpgradeCLRHeader**|CLR üstbilgisini 2.5 sürümüne yükseltir. **Not:** derlemeler CLR üstbilgi sürüm 2.5 veya yerel olarak çalıştırmak daha büyük olmalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hiçbir seçenek belirtilmezse, CorFlags Dönüştürme aracı belirtilen derleme için bayrakları görüntüler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [64 bit Uygulamalar](../../../docs/framework/64-bit-apps.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
