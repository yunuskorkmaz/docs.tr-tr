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
ms.openlocfilehash: 46e846eaf92835fb2a9130b85ed20749934ca5a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715724"
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe (Yalıtılmış Depolama Aracı)
Yalıtılmış Depolama aracı, geçerli kullanıcı için varolan tüm depoları listeler veya kaldırır.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/h**[**elp**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/liste**|Geçerli kullanıcı için varolan tüm depoları görüntüler. Buna, kullanıcı tarafından çalıştırılan tüm uygulamaların veya derlemelerin depoları dahildir.|  
|**/makine**|Makine deposunu seçer. Eylemin makine deposuna uygulanması gerektiğini belirtmek için **/list** veya **/remove** seçeneğiyle bu seçeneği kullanın.<br /><br /> .NET Framework 2.0'da yeni bir özelliktir|  
|**/sessiz**|Sessiz mod kullanılacağını belirtir; yalnızca hata iletileri görünecek şekilde bilgilendirici çıktıyı engeller.|  
|**/kaldırmak**|Geçerli kullanıcı için varolan tüm depoları kalıcı olarak kaldırır.|  
|**/dolaşım**|Dolaşım deposunu seçer. Eylemin dolaşım mağazasına uygulanması gerektiğini belirtmek için **/list** veya **/remove** seçenekleriyle bu seçeneği kullanın.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Herhangi bir seçenek belirtmeden Storeadm.exe'yi komut satırından çalıştırmak sözdizimini ve araç için seçenekleri görüntüler.  
  
 **/list** ve **/remove** seçenekleri genellikle birer birer kullanılır; ancak, iki veya daha fazla seçenek belirtilirse, bunlar komut satırında göründükleri sırada gerçekleştirilir.  
  
 Uygulamaların, bir kullanıcı için iki depodan birine veya makine deposuna kaydetme seçeneği vardır:  
  
- Yerel mağaza, kullanıcı verileri dolaşımı kullanıcı için etkinleştirilse bile (Windows 2000 ve sonraki yerlerde) gezinmemesi garanti edilen bir konumda bulunur.  
  
- Dolaşım deposu, gezinmeyi yapabilen bir konumda bulunur, ancak bunu ancak Windows NT yönetimi aracılığıyla kullanıcı için dolaşım etkinleştirilirse yapabilir.  
  
- Makine deposu bir makinedeki tüm kullanıcılar için ortaktır ve o makinede ortak bir dizin altında depolanır.  
  
    > [!NOTE]
    > Makine deposu .NET Framework sürüm 2.0'da yeni bir özelliktir.  
  
 Dolaşımın kullanıcı için etkinleştirilip etkinleştirilmediği Storeadm.exe'nin yönetimini etkilemez. Aracı hiçbir seçenek olmadan çalıştırmak yerel depoya tüm işlemleri uygular. Aracı **/dolaşım** seçeneğiyle çalıştırmak, dolaşıma sabilen mağazaya tüm eylemleri uygular. /machine seçeneği **/machine** ile aracı çalıştırmak makine deposuna tüm eylemleri uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Yalıtılmış Depolama](../../standard/io/isolated-storage.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
