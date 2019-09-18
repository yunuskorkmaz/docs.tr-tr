---
title: Çalışma Zamanı Bilgileri ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- runtime information events [.NET Framework]
- ETW, runtime information events
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ab3844b293d09cec02236fb9befd836aa4113ea
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046223"
---
# <a name="runtime-information-etw-events"></a>Çalışma Zamanı Bilgileri ETW Olayları
Bu ETW olayları, çalışma zamanı hakkındaki SKU, sürüm numarası, çalışma zamanının etkinleştirildiği yol, ile başlatıldığı komut satırı parametreleri, GUID (varsa) ve diğer ilgili bilgiler dahil olmak üzere çalışma zamanı hakkındaki bilgileri günlüğe kaydeder. Bir işlem içinde birden çok çalışma alanı yürütülerek, bu olaylar tarafından sunulan bilgiler (ClrInstanceID) çalışma zamanlarının belirsizliğini ortadan kaldırmaya yardımcı olur.  
  
 Aşağıdaki tabloda iki çalışma zamanı bilgi olayı gösterilmektedir. Olaylar herhangi bir anahtar sözcük veya maske altında oluşturulabilir. (Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)  
  
|Olay|Olay Kimliği|Sağlayıcı|Açıklama|  
|-----------|--------------|--------------|-----------------|  
|`RuntimeInformationEvent`|187|CLRRuntime|Çalışma zamanı yüklendiğinde tetiklenir.|  
|`RuntimeInformationDCStart`|187|Clrrunaşağı|Yüklenen çalışma zamanlarını numaralandırır.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
|İsteyin|Win: UInt16|1 – Masaüstü CLR.<br /><br /> 2 – CoreCLR.|  
|BclVersion – ana sürüm|Win: UInt16|Mscorlib. dll ' nin ana sürümü.|  
|BclVersion – Ikincil sürüm|Win: UInt16|Mscorlib. dll ' nin ikincil sürüm numarası.|  
|BclVersion – derleme numarası|Win: UInt16|Mscorlib. dll ' nin derleme numarası.|  
|BclVersion – QFE|Win: UInt16|Mscorlib. dll ' nin düzeltme sürümü numarası.|  
|VMVersion – ana sürüm|Win: UInt16|SKU 'ya bağlı olarak CLR. dll veya CoreCLR. dll sürümü.|  
|VMVersion – Ikincil sürüm|Win: UInt16|SKU 'ya bağlı olarak CLR. dll veya CoreCLR. dll ' nin ikincil sürümü.|  
|VMVersion – derleme numarası|Win: UInt16|Clr. dll veya CoreCLR. dll derleme numarası.|  
|VMVersion – QFE|Win: UInt16|Clr. dll veya CoreCLR. dll ' nin düzeltme sürümü numarası.|  
|StartupFlags|Win: UInt32|Mscoree. h içinde tanımlanan başlangıç bayrakları.|  
|StartupMode|Win: UInt8|0x01 tarafından yönetilen yürütülebilir.<br /><br /> 0x02 tarafından barındırılan CLR.<br /><br /> 0x04- C++ yönetilen birlikte çalışma.<br /><br /> 0x08-COM-etkinleştirildi.<br /><br /> 0x10-Diğer.|  
|Komut satırı|Win: UnicodeString|Yalnızca StartupMode = 0x01 null olmayan bir değer.|  
|ComObjectGUID|Win: GUID|Yalnızca StartupMode = 0x08 ise null değil.|  
|RuntimeDLLPath|Win: UnicodeString|İşleme yüklenmiş CLR. dll dosyasının yolu.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
