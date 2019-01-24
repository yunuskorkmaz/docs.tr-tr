---
title: Clrver.exe (CLR Sürüm Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5543e49ea44c20a536a7097277b246d4041522a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735441"
---
# <a name="clrverexe-clr-version-tool"></a>Clrver.exe (CLR Sürüm Aracı)
CLR Sürüm aracı (Clrver.exe) ortak dil çalışma zamanının (CLR) bilgisayarda yüklü tüm sürümlerini bildirir.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
clrver [option]  
```  
  
## <a name="options"></a>Seçenekler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`-all`|Bilgisayarda CLR'yi kullanan tüm işlemleri görüntüler.|  
|*PID*|Belirtilen işlem kimliğine (PID) sahip işlem tarafından kullanılan CLR'nin sürümlerini görüntüler.|  
|`-?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Clrver.exe'yi hiçbir seçenek olmadan çağırırsanız, yüklü tüm CLR sürümlerini görüntüler. Başka bir kullanıcı için bir PID belirtirseniz, sürüm bilgisi elde etmek için yönetici izinlerinizin olması gerekir.  
  
> [!NOTE]
>  Windows Vista ve sonraki sürümlerde, Kullanıcı Hesabı Denetimi (UAC) bir kullanıcının ayrıcalıkları belirler. Yerleşik Yöneticiler grubunun bir üyesi iseniz, size iki çalışma zamanı erişim belirteci atanır: Standart kullanıcı erişim belirteci ve yönetici erişim belirteci. Varsayılan olarak, standart kullanıcı rolünde olursunuz. Yönetici izni gerektiren kodları yürütmek için önce ayrıcalıklarınızı standart kullanıcıdan yöneticiye yükseltmeniz gerekir. Komut istemi simgesini sağ tıklatıp komut istemini başlattıktan sonra, yönetici olarak çalıştırmak istediğinizi belirterek bunu yapabilirsiniz.  
  
 SYSTEM, LOCAL SERVICE ve NETWORK SERVICE işlemlerinin CLR sürümünü belirlemeye çalışmak PID'in varolmadığını belirten bir ileti alınmasına neden olur.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut bilgisayarda yüklü tüm CLR sürümlerini görüntüler.  
  
 `clrver`  
  
 Aşağıdaki komut, işlem 128 tarafından kullanılan CLR sürümünü görüntüler.  
  
 `clrver 128`  
  
 Aşağıdaki komut, yönetilen tüm işlemleri ve kullanmakta oldukları CLR sürümünü görüntüler.  
  
 `Clrver -all`  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Araçlar](../../../docs/framework/tools/index.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
