---
title: CorFlags.exe (CorFlags Dönüştürme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: e1251b6660db45f3af4f6e57114b1b10da18bd0a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129856"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (CorFlags Dönüştürme Aracı)
CorFlags Dönüştürme aracı, taşınabilir çalıştırılabilir bir görüntünün üstbilgisinin CorFlags bölümünü yapılandırmanıza olanak verir.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
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
|:------------|-----------------|  
|`-32BIT[REQ]+`|32BITREQUIRED bayrağını ayarlar.|  
|`-32BIT[REQ]-`|32BITREQUIRED bayrağını kaldırır.|  
|`-32BITPREF+`|32BITPREFERRED bayrağını ayarlar. Uygulama 64-bit platformlarda dahi 32-bit işlem olarak çalışır. Bu bayrağı yalnızca EXE dosyalarında ayarlayın. Bayrak bir DLL üzerinde ayarlanmışsa, DLL 64 bit işlemlerinde <xref:System.BadImageFormatException> yüklenmez ve bir özel durum atılır. Bu bayrağı içeren bir EXE dosyası bir 64-bit işleme yüklenebilir.<br /><br /> .NET Framework 4.5'te yeni.|  
|`-32BITPREF-`|32BITPREFERRED bayrağını kaldırır.<br /><br /> .NET Framework 4.5'te yeni.|  
|`-?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`-Force`|Derleme bir tanımlayıcı adla adlandırılmış olsa da bir güncelleştirmenin yapılmasını sağlar. **Önemli:**  Güçlü adlandırılmış bir derlemeyi güncellerseniz, kodunu yürütmeden önce yeniden imzalamanız gerekir.|  
|`-help`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`-ILONLY+`|ILONLY bayrağını ayarlar.|  
|`-ILONLY-`|ILONLY bayrağını kaldırır.|  
|`-nologo`|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|`-RevertCLRHeader`|CLR üstbilgisini 2.0 sürümüne döndürür.|  
|`-UpgradeCLRHeader`|CLR üstbilgisini 2.5 sürümüne yükseltir. **Not:**  Derlemelerin yerel olarak çalıştırılabilmek için 2,5 veya daha büyük bir CLR üstbilgi sürümü ne olmalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hiçbir seçenek belirtilmezse, CorFlags Dönüştürme aracı belirtilen derleme için bayrakları görüntüler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [64 bit Uygulamalar](../64-bit-apps.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
