---
title: Çalışma Zamanı Bilgileri ETW Olayları
description: SKU, sürüm numarasını, çalışma zamanının nasıl etkinleştirildiğini (komut satırı parametreleri dahil), GUID 'yi ve daha fazlasını kaydeden çalışma zamanı bilgileri ETW olaylarına bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- runtime information events [.NET Framework]
- ETW, runtime information events
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
ms.openlocfilehash: 385519229bdb76841cdf592d95e96d2288ec5e1a
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474234"
---
# <a name="runtime-information-etw-events"></a>Çalışma Zamanı Bilgileri ETW Olayları
Bu ETW olayları, çalışma zamanı hakkındaki SKU, sürüm numarası, çalışma zamanının etkinleştirildiği yol, ile başlatıldığı komut satırı parametreleri, GUID (varsa) ve diğer ilgili bilgiler dahil olmak üzere çalışma zamanı hakkındaki bilgileri günlüğe kaydeder. Bir işlem içinde birden çok çalışma alanı yürütülerek, bu olaylar tarafından sunulan bilgiler (ClrInstanceID) çalışma zamanlarının belirsizliğini ortadan kaldırmaya yardımcı olur.  
  
 Aşağıdaki tabloda iki çalışma zamanı bilgi olayı gösterilmektedir. Olaylar herhangi bir anahtar sözcük veya maske altında oluşturulabilir. (Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)  
  
|Olay|Olay Kimliği|Sağlayıcı|Description|  
|-----------|--------------|--------------|-----------------|  
|`RuntimeInformationEvent`|187|CLRRuntime|Çalışma zamanı yüklendiğinde tetiklenir.|  
|`RuntimeInformationDCStart`|187|Clrrunaşağı|Yüklenen çalışma zamanlarını numaralandırır.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Description|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
|Sku|Win: UInt16|1 – Masaüstü CLR.<br /><br /> 2 – CoreCLR.|  
|BclVersion – ana sürüm|Win: UInt16|mscorlib.dll ana sürümü.|  
|BclVersion – Ikincil sürüm|Win: UInt16|mscorlib.dll ikincil sürüm numarası.|  
|BclVersion – derleme numarası|Win: UInt16|mscorlib.dll yapı numarası.|  
|BclVersion – QFE|Win: UInt16|mscorlib.dll düzeltme sürümü numarası.|  
|VMVersion – ana sürüm|Win: UInt16|SKU 'ya bağlı olarak clr.dll veya coreclr.dll sürümü.|  
|VMVersion – Ikincil sürüm|Win: UInt16|SKU 'ya bağlı olarak clr.dll veya coreclr.dll ikincil sürümü.|  
|VMVersion – derleme numarası|Win: UInt16|clr.dll veya coreclr.dll derleme sayısı.|  
|VMVersion – QFE|Win: UInt16|clr.dll veya coreclr.dll düzeltme sürümü numarası.|  
|StartupFlags|Win: UInt32|Mscoree. h içinde tanımlanan başlangıç bayrakları.|  
|StartupMode|Win: UInt8|0x01 tarafından yönetilen yürütülebilir.<br /><br /> 0x02 tarafından barındırılan CLR.<br /><br /> 0x04-C++ Managed Interop.<br /><br /> 0x08-COM-etkinleştirildi.<br /><br /> 0x10-Diğer.|  
|CommandLine|Win: UnicodeString|Yalnızca StartupMode = 0x01 null olmayan bir değer.|  
|ComObjectGUID|Win: GUID|Yalnızca StartupMode = 0x08 ise null değil.|  
|RuntimeDLLPath|Win: UnicodeString|İşleme yüklenmiş CLR. dll dosyasının yolu.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
