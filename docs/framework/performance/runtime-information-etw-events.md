---
title: Çalışma Zamanı Bilgileri ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- runtime information events [.NET Framework]
- ETW, runtime information events
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4244196a957c67a807cdb705f6d74ee2b41869d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391608"
---
# <a name="runtime-information-etw-events"></a>Çalışma Zamanı Bilgileri ETW Olayları
Bu ETW olayları SKU, sürüm numarası, hangi çalışma zamanı etkinleştirildi, şekilde de dahil olmak üzere çalışma zamanı, GUID ile (varsa), başlatıldığından komut satırı parametreleri hakkında bilgi ve diğer ilgili bilgileri kaydeder. Bir işlemde birden çok çalışma zamanları çalıştırıldığında bu olayları (ClrInstanceID) tarafından sağlanan bilgileri çalışma zamanları belirsizliğini ortadan kaldırmak yardımcı olur.  
  
 Aşağıdaki tabloda iki çalışma zamanı bilgileri olayları gösterir. Olaylar, herhangi bir anahtar sözcüğü veya maskesi altında yükseltilebilir. (Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olay|Olay Kimliği|Sağlayıcı|Açıklama|  
|-----------|--------------|--------------|-----------------|  
|`RuntimeInformationEvent`|187|CLRRuntime|Bir çalışma zamanı yüklendi tetiklenir.|  
|`RuntimeInformationDCStart`|187|CLRRundown|Yüklenen çalışma zamanları numaralandırır.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
|SKU|Win: UInt16|1 – Masaüstü CLR.<br /><br /> 2 – CoreCLR.|  
|BclVersion – ana sürümü|Win: UInt16|Mscorlib.dll ana sürümü.|  
|BclVersion – alt sürümü|Win: UInt16|Mscorlib.dll ikincil sürüm numarası.|  
|BclVersion – yapı numarası|Win: UInt16|Mscorlib.dll sayısı oluşturun.|  
|BclVersion – QFE|Win: UInt16|Mscorlib.dll düzeltme sürüm numarası.|  
|VMVersion – ana sürümü|Win: UInt16|Clr.dll veya SKU bağlı olarak coreclr.dll sürümü.|  
|VMVersion – alt sürümü|Win: UInt16|Clr.dll veya coreclr.dll SKU bağlı olarak küçük sürümü.|  
|VMVersion – yapı numarası|Win: UInt16|Yapı numarası clr.dll veya coreclr.dll.|  
|VMVersion – QFE|Win: UInt16|Clr.dll veya coreclr.dll düzeltme sürüm numarası.|  
|StartupFlags|Win: UInt32|Başlangıç bayraklar mscoree.h tanımlanmış.|  
|StartupMode|Win: UInt8|0x01 - yönetilen çalıştırılabilir.<br /><br /> 0x02 - barındırılan CLR.<br /><br /> 0x04 - C++ birlikte çalışma yönetilen.<br /><br /> 0x08 - COM etkinleştirildi.<br /><br /> 0x10 - diğer.|  
|komut satırı|Win: UnicodeString|Null olmayan eksikse StartupMode 0x01 =.|  
|ComObjectGUID|Win: GUID|Null olmayan eksikse StartupMode 0x08 =.|  
|RuntimeDLLPath|Win: UnicodeString|İşlemine yüklendi CLR .dll dosyasının yolu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
