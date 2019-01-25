---
title: Çalışma Zamanı Bilgileri ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- runtime information events [.NET Framework]
- ETW, runtime information events
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb213ef4a335cf6784c2889cd9cf0214a1411da2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735720"
---
# <a name="runtime-information-etw-events"></a>Çalışma Zamanı Bilgileri ETW Olayları
Bu ETW olayları SKU, sürüm numarası, hangi çalışma zamanı etkinleştirildi, şekilde dahil olmak üzere çalışma zamanı, GUID, (varsa), ile başlatıldığından komut satırı parametreleri hakkında bilgi ve diğer ilgili bilgileri kaydeder. Bir işlem içinde birden çok çalışma zamanları yürütülüyorsa, bu olaylar (ClrInstanceID) tarafından sağlanan bilgiler, çalışma zamanları belirsizliğinin ortadan kaldırılmasını yardımcı olur.  
  
 Aşağıdaki tabloda iki çalışma zamanı bilgileri olayları gösterir. Olaylar, herhangi bir anahtar sözcüğü veya maskesi altında yükseltilebilir. (Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olay|Olay Kimliği|Sağlayıcı|Açıklama|  
|-----------|--------------|--------------|-----------------|  
|`RuntimeInformationEvent`|187|CLRRuntime|Bir çalışma zamanı yüklendiğinde oluşturulur.|  
|`RuntimeInformationDCStart`|187|CLRRundown|Yüklenen çalışma zamanları numaralandırır.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
|SKU|Kazanma: UInt16|1 – Masaüstü CLR.<br /><br /> 2 – CoreCLR.|  
|BclVersion – ana sürümü|Kazanma: UInt16|Mscorlib.dll ana sürümü.|  
|BclVersion – alt sürümü|Kazanma: UInt16|Mscorlib.dll alt sürüm sayısı.|  
|BclVersion – derleme numarası|Kazanma: UInt16|Derleme numarası sağlar.|  
|BclVersion – QFE|Kazanma: UInt16|Mscorlib.dll düzeltme sürüm numarası.|  
|VMVersion – ana sürümü|Kazanma: UInt16|Clr.dll veya SKU bağlı olarak, coreclr.dll sürümü.|  
|VMVersion – alt sürümü|Kazanma: UInt16|Clr.dll veya coreclr.dll, SKU bağlı olarak ikincil sürümü.|  
|VMVersion – derleme numarası|Kazanma: UInt16|Derleme numarası clr.dll veya coreclr.dll.|  
|VMVersion – QFE|Kazanma: UInt16|Clr.dll veya coreclr.dll düzeltme sürüm numarası.|  
|StartupFlags|Kazanma: UInt32|Mscoree.h içinde tanımlanan başlangıç bayraklar.|  
|StartupMode|Kazanma: UInt8|0x01 - yönetilen çalıştırılabilir.<br /><br /> 0x02 - barındırılan CLR.<br /><br /> 0x04 - C++ birlikte çalışması yönetilen.<br /><br /> 0x08 - COM etkinleştirildi.<br /><br /> 0x10 - diğer.|  
|komut satırı|Kazanma: UnicodeString|Null olmayan yalnızca şu durumlarda StartupMode 0x01 =.|  
|ComObjectGUID|Kazanma: GUID|Null olmayan yalnızca şu durumlarda StartupMode 0x08 =.|  
|RuntimeDLLPath|Kazanma: UnicodeString|İşlem yüklenmiş CLR .dll dosyasının yolu.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
