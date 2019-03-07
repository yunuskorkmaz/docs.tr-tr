---
title: Storeadm.exe (Yalıtılmış Depolama Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 13640e508dafe28b53f4254656afe744b90a2eb2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491483"
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe (Yalıtılmış Depolama Aracı)
Yalıtılmış Depolama aracı, geçerli kullanıcı için varolan tüm depoları listeler veya kaldırır.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/h**[**elp**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/ List**|Geçerli kullanıcı için varolan tüm depoları görüntüler. Buna, kullanıcı tarafından çalıştırılan tüm uygulamaların veya derlemelerin depoları dahildir.|  
|**/ MACHINE**|Makine deposunu seçer. Bu seçeneği kullanın **/list** veya **/remove** işlemin makine deposuna da uygulanacağını belirtmek için seçeneği.<br /><br /> .NET Framework 2.0'da yeni bir özelliktir|  
|**/quiet**|Sessiz mod kullanılacağını belirtir; yalnızca hata iletileri görünecek şekilde bilgilendirici çıktıyı engeller.|  
|**/ Remove**|Geçerli kullanıcı için varolan tüm depoları kalıcı olarak kaldırır.|  
|**/ roaming**|Dolaşım deposunu seçer. Bu seçeneği kullanın **/list** veya **/remove** işlemin Dolaşım deposuna uygulanacağını belirtmek için Seçenekler.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Herhangi bir seçenek belirtmeden Storeadm.exe'yi komut satırından çalıştırmak sözdizimini ve araç için seçenekleri görüntüler.  
  
 **/List** ve **/remove** seçenekleri genellikle kullanılan birer birer; iki veya daha fazla seçeneği belirtilmişse ancak bunlar komut satırında göründükleri sırayla gerçekleştirilir.  
  
 Uygulamaların, bir kullanıcı için iki depodan birine veya makine deposuna kaydetme seçeneği vardır:  
  
-   Kullanıcı verileri dolaşımı kullanıcı için etkinleştirilmiş olsa dahi (Windows 2000 ve sonraki sürümlerde) Dolaşımda olmayacağı garantili bir konumda yerel depo yok.  
  
-   Dolaşım deposu, Dolaşımda olabilen bir konumda var, ancak Dolaşım kullanıcı Windows NT Yönetimi yoluyla etkinleştirilmişse yalnızca bunu yapabilirsiniz.  
  
-   Makine deposu bir makinedeki tüm kullanıcılar için ortaktır ve o makinede ortak bir dizin altında depolanır.  
  
    > [!NOTE]
    >  Makine deposu .NET Framework sürüm 2.0'da yeni bir özelliktir.  
  
 Dolaşımın kullanıcı için etkinleştirilip etkinleştirilmediği Storeadm.exe'nin yönetimini etkilemez. Aracı hiçbir seçenek olmadan çalıştırmak yerel depoya tüm işlemleri uygular. Aracı ile çalışan **/ roaming** seçeneği, Dolaşımda olabilen depoya tüm işlemleri uygular. Aracı ile çalışan **/makine** seçeneği makine deposuna tüm işlemleri uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Araçlar](../../../docs/framework/tools/index.md)
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
