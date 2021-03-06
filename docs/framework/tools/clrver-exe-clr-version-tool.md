---
title: Clrver.exe (CLR Sürüm Aracı)
description: CLR sürüm aracını Clrver.exe gözden geçirin. Bu araç, bilgisayardaki ortak dil çalışma zamanının (CLR) yüklü tüm sürümlerini raporlar.
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
ms.openlocfilehash: 8205b92f3997f6abacc566e2e6f2b37604fbda07
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255255"
---
# <a name="clrverexe-clr-version-tool"></a>Clrver.exe (CLR Sürüm Aracı)

CLR Sürüm aracı (Clrver.exe) ortak dil çalışma zamanının (CLR) bilgisayarda yüklü tüm sürümlerini bildirir.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, [geliştiriciler için bir komut satırı kabuğu](/visualstudio/ide/reference/command-prompt-powershell)kullanın.  
  
 Komut isteminde aşağıdaki komutu girin:  
  
## <a name="syntax"></a>Syntax  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a>Seçenekler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`-all`|Bilgisayarda CLR'yi kullanan tüm işlemleri görüntüler.|  
|*Kişisel*|Belirtilen işlem kimliğine (PID) sahip işlem tarafından kullanılan CLR'nin sürümlerini görüntüler.|  
|`-?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  

 Clrver.exe'yi hiçbir seçenek olmadan çağırırsanız, yüklü tüm CLR sürümlerini görüntüler. Başka bir kullanıcı için bir PID belirtirseniz, sürüm bilgisi elde etmek için yönetici izinlerinizin olması gerekir.  
  
> [!NOTE]
> Windows Vista ve sonraki sürümlerde, Kullanıcı Hesabı Denetimi (UAC) bir kullanıcının ayrıcalıkları belirler. Yerleşik Yöneticiler grubunun bir üyesi iseniz, size iki çalışma zamanı erişim belirteci atanır: Standart kullanıcı erişim belirteci ve yönetici erişim belirteci. Varsayılan olarak, standart kullanıcı rolünde olursunuz. Yönetici izni gerektiren kodları yürütmek için önce ayrıcalıklarınızı standart kullanıcıdan yöneticiye yükseltmeniz gerekir. Komut istemi simgesini sağ tıklatıp komut istemini başlattıktan sonra, yönetici olarak çalıştırmak istediğinizi belirterek bunu yapabilirsiniz.  
  
 SYSTEM, LOCAL SERVICE ve NETWORK SERVICE işlemlerinin CLR sürümünü belirlemeye çalışmak PID'in varolmadığını belirten bir ileti alınmasına neden olur.  
  
## <a name="examples"></a>Örnekler  

 Aşağıdaki komut bilgisayarda yüklü tüm CLR sürümlerini görüntüler.  
  
 `clrver`  
  
 Aşağıdaki komut, işlem 128 tarafından kullanılan CLR sürümünü görüntüler.  
  
 `clrver 128`  
  
 Aşağıdaki komut, yönetilen tüm işlemleri ve kullanmakta oldukları CLR sürümünü görüntüler.  
  
 `Clrver -all`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Geliştirici komut satırı kabukları](/visualstudio/ide/reference/command-prompt-powershell)
