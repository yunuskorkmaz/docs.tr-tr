---
title: CorFlags.exe (CorFlags Dönüştürme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b420fb451bf1bb2078a4419a648a1407c39ad178
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044747"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (CorFlags Dönüştürme Aracı)
CorFlags Dönüştürme aracı, taşınabilir çalıştırılabilir bir görüntünün üstbilgisinin CorFlags bölümünü yapılandırmanıza olanak verir.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Gerekli parametre|Açıklama|  
|------------------------|-----------------|  
|`assembly`|CorFlags'in yapılandırılacağı derlemenin adı.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/32BIT [REQ] +**|32BITREQUIRED bayrağını ayarlar.|  
|**/32BIT [REQ]-**|32BITREQUIRED bayrağını kaldırır.|  
|**/32BITPREF +**|32BITPREFERRED bayrağını ayarlar. Uygulama 64-bit platformlarda dahi 32-bit işlem olarak çalışır. Bu bayrağı yalnızca EXE dosyalarında ayarlayın. Bayrak dll üzerinde ayarlandıysa, dll 64-bit işlemlerde yüklenemez ve bir <xref:System.BadImageFormatException> özel durum oluşur. Bu bayrağı içeren bir EXE dosyası bir 64-bit işleme yüklenebilir.<br /><br /> .NET Framework 4,5 ' de yenidir.|  
|**/32BITTERCIH-**|32BITPREFERRED bayrağını kaldırır.<br /><br /> .NET Framework 4,5 ' de yenidir.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/Force**|Derleme bir tanımlayıcı adla adlandırılmış olsa da bir güncelleştirmenin yapılmasını sağlar. **Önemli:**  Tanımlayıcı bir adla adlandırılmış bir derlemeyi güncelleştirirseniz, kodunu yürütülmeden önce onu tekrar imzalamanız gerekir.|  
|**/ Help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/ILONLY +**|ILONLY bayrağını ayarlar.|  
|**ILONLY**|ILONLY bayrağını kaldırır.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/RevertCLRHeader**|CLR üstbilgisini 2.0 sürümüne döndürür.|  
|**/UpgradeCLRHeader**|CLR üstbilgisini 2.5 sürümüne yükseltir. **Not:**  Yerel olarak çalışması için derlemelerde CLR üstbilgi sürümü 2.5 veya daha üstü olmalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hiçbir seçenek belirtilmezse, CorFlags Dönüştürme aracı belirtilen derleme için bayrakları görüntüler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [64 bit Uygulamalar](../64-bit-apps.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
