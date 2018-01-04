---
title: "Nasıl yapılır: Genel Derleme Önbelleğinin İçeriğini Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b4cc4b1a3e68d6d39e13a56b2a519d15b72bd3a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Nasıl yapılır: Genel Derleme Önbelleğinin İçeriğini Görüntüleme
Kullanım [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) genel derleme önbelleğinin içeriğini görüntülemek için.  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a>Genel derleme önbelleğinde derleme listesi görüntülemek için  
  
1.  Konumundaki [Visual Studio komut istemi](../../../docs/framework/tools/developer-command-prompt-for-vs.md), aşağıdaki komutu yazın:  
  
     **Gacutil -m**   
     veya  
    **Gacutil /l**  
  
 .NET Framework'ün önceki sürümlerindeki [Shfusion.dll](http://msdn.microsoft.com/en-us/0d9464cf-ddba-4ca9-bbec-f678fb58f380) Windows kabuk uzantısı, Genel Derleme Önbelleği dosya Gezgini'nde görüntülemek etkin. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll artık kullanılmıyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
