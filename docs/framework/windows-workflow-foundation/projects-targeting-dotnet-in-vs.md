---
title: Proje .NET Framework 3.0 ve 3.5 Visual Studio 2010 hedefleme yazma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6dc6657bad5cc11eaa723c733319673468749b79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a>Proje .NET Framework 3.0 ve 3.5 Visual Studio 2010 hedefleme yazma
Kullanabileceğiniz [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] hedefleyen projeler oluşturmak için [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sürüm 3.0 veya 3.5. Bu konu bunun nasıl yapılacağını açıklar.  
  
> [!NOTE]
>  Etkinlikler eklerken emin olun istenen sürümüyle [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ayarlanır. İş akışı hedef sürümü etkinlikleri eklendikten sonra değiştirilmesi başarısız doğrulama da iş akışı neden olur.  
  
> [!WARNING]
>  Var olan iş akışlarında açma [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] sahip olan .net Framework 3.5 etkinlikleri sırasında bir hata neden olacak `this.SetValue()`. .Net önceki sürümleriyle oluşturulan projeleri açabilmek Framework, önce boş bir iş akışı Tasarımcısı'nda açın ve bir .net ekleyin Framework 3.5 etkinlik.  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a>Visual Studio 2010 ile .NET Framework 3.0 veya 3.5 proje oluşturmak için  
  
1.  Açık [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Seçin **dosya**, **yeni**, **proje**.  
  
3.  İletişim kutusunun üstündeki aşağı açılan listesinde, istediğiniz sürümü seçin [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a>.NET Framework'ün hedeflenen sürümüne yükseltmek için  
  
1.  Çözüm Gezgini'nde projeye sağ tıklayın ve seçin **özellikleri**.  
  
2.  İçinde **hedef Framework** aşağı açılan listesinde, istediğiniz sürümü seçin.
