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
ms.openlocfilehash: 3c9b8d0680a50d9945bef0d03d10e45750fc49a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe (Yalıtılmış Depolama Aracı)
Yalıtılmış Depolama aracı, geçerli kullanıcı için varolan tüm depoları listeler veya kaldırır.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/h**[**ardım**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/ List**|Geçerli kullanıcı için varolan tüm depoları görüntüler. Buna, kullanıcı tarafından çalıştırılan tüm uygulamaların veya derlemelerin depoları dahildir.|  
|**/ Makine**|Makine deposunu seçer. Bu seçenek ile kullanmak **/list** veya **/Kaldır** eylemi makine deposuna uygulamalıdır belirtmek için seçeneği.<br /><br /> .NET Framework 2.0'da yeni bir özelliktir|  
|**/quiet**|Sessiz mod kullanılacağını belirtir; yalnızca hata iletileri görünecek şekilde bilgilendirici çıktıyı engeller.|  
|**/ Remove**|Geçerli kullanıcı için varolan tüm depoları kalıcı olarak kaldırır.|  
|**/ Dolaşım**|Dolaşım deposunu seçer. Bu seçenek ile kullanmak **/list** veya **/Kaldır** eylemi gezici deposuna uygulamalıdır belirtmek için Seçenekler.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Herhangi bir seçenek belirtmeden Storeadm.exe'yi komut satırından çalıştırmak sözdizimini ve araç için seçenekleri görüntüler.  
  
 **/List** ve **/Kaldır** seçenekleri genellikle kullanılan birer birer; iki veya daha fazla seçenek belirtilmezse, ancak bunlar komut satırında göründükleri sırada gerçekleştirilir.  
  
 Uygulamaların, bir kullanıcı için iki depodan birine veya makine deposuna kaydetme seçeneği vardır:  
  
-   Kullanıcı için gezici kullanıcı verileri etkin olsa bile (Windows 2000 ve daha sonra) dolaştırmamayı garanti bir konumda yerel deposu bulunmaktadır.  
  
-   Dolaşım deposu dolaşan kurabilen bir konumda var, ancak Windows NT Yönetim aracılığıyla kullanıcı için gezici etkinse, yalnızca bunu yapabilirsiniz.  
  
-   Makine deposu bir makinedeki tüm kullanıcılar için ortaktır ve o makinede ortak bir dizin altında depolanır.  
  
    > [!NOTE]
    >  Makine deposu .NET Framework sürüm 2.0'da yeni bir özelliktir.  
  
 Dolaşımın kullanıcı için etkinleştirilip etkinleştirilmediği Storeadm.exe'nin yönetimini etkilemez. Aracı hiçbir seçenek olmadan çalıştırmak yerel depoya tüm işlemleri uygular. Aracı ile çalışan **/ gezici** seçeneği dolaşabilir deposu tüm eylemleri uygular. Aracı ile çalışan **/makine** seçeneği makine deposuna tüm eylemleri uygular.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
