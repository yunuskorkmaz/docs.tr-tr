---
title: CorFlags.exe (CorFlags Dönüştürme Aracı)
description: CorFlags dönüştürme aracı CorFlags.exe anlayın. Bu araç taşınabilir bir yürütülebilir görüntünün üst bilgisinin CorFlags bölümünü yapılandırmanızı sağlar.
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: 4481e6718372fe7b58dbc05ab7cfe35e6d3047ce
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258058"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (CorFlags Dönüştürme Aracı)

CorFlags Dönüştürme aracı, taşınabilir çalıştırılabilir bir görüntünün üstbilgisinin CorFlags bölümünü yapılandırmanıza olanak verir.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, [geliştiriciler için bir komut satırı kabuğu](/visualstudio/ide/reference/command-prompt-powershell)kullanın.  
  
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
|`-32BITPREF+`|32BITPREFERRED bayrağını ayarlar. Uygulama 64-bit platformlarda dahi 32-bit işlem olarak çalışır. Bu bayrağı yalnızca EXE dosyalarında ayarlayın. Bayrak DLL üzerinde ayarlandıysa, DLL 64-bit işlemlerde yüklenemez ve bir <xref:System.BadImageFormatException> özel durum oluşur. Bu bayrağı içeren bir EXE dosyası bir 64-bit işleme yüklenebilir.<br /><br /> .NET Framework 4,5 ' de yenidir.|  
|`-32BITPREF-`|32BITPREFERRED bayrağını kaldırır.<br /><br /> .NET Framework 4,5 ' de yenidir.|  
|`-?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`-Force`|Derleme bir tanımlayıcı adla adlandırılmış olsa da bir güncelleştirmenin yapılmasını sağlar. **Önemli:**  Tanımlayıcı adlı bir derlemeyi güncelleştirirseniz kodu yürütmeden önce yeniden imzalamanız gerekir.|  
|`-help`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`-ILONLY+`|ILONLY bayrağını ayarlar.|  
|`-ILONLY-`|ILONLY bayrağını kaldırır.|  
|`-nologo`|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|`-RevertCLRHeader`|CLR üstbilgisini 2.0 sürümüne döndürür.|  
|`-UpgradeCLRHeader`|CLR üstbilgisini 2.5 sürümüne yükseltir. **Note:**  Derlemeler yerel olarak çalıştırmak için 2,5 veya daha büyük bir CLR üstbilgi sürümüne sahip olmalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Hiçbir seçenek belirtilmezse, CorFlags Dönüştürme aracı belirtilen derleme için bayrakları görüntüler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [64 bit Uygulamalar](../64-bit-apps.md)
- [Geliştirici komut satırı kabukları](/visualstudio/ide/reference/command-prompt-powershell)
