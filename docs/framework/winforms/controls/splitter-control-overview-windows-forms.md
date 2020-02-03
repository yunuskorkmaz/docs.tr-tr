---
title: Bölümlendirici Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 3d6da8daf9bb0e8df4f69554a87725a7ddb65acb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742893"
---
# <a name="splitter-control-overview-windows-forms"></a>Bölümlendirici Denetimine Genel Bakış (Windows Forms)
> [!IMPORTANT]
> <xref:System.Windows.Forms.SplitContainer>, önceki sürümlerin <xref:System.Windows.Forms.Splitter> denetimine işlevsellik koyar, ancak bunu seçerseniz, <xref:System.Windows.Forms.Splitter> hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.  
  
 Windows Forms <xref:System.Windows.Forms.Splitter> denetimleri çalışma zamanında yerleşik denetimleri yeniden boyutlandırmak için kullanılır. <xref:System.Windows.Forms.Splitter> denetimi genellikle, veri bölmeleri farklı zamanlarda değişen genişlikler hakkında bilgi içeren Windows Gezgini gibi çeşitli veri uzunluklarına sahip denetimlerle birlikte kullanılır.  
  
## <a name="working-with-the-splitter-control"></a>Splitter denetimiyle çalışma  
 Kullanıcı, bir denetimin bir Splitter denetimi tarafından yeniden boyutlandırılabileceği bir denetimin yerleştirilmemiş kenarında fare işaretçisini işaret ediyorsa, işaretçiyi denetimin yeniden boyutlandırılabileceğini belirtmek için görünümünü değiştirir. Bölümlendirici denetimi ile, Kullanıcı hemen öncesindeki yerleşik denetimi yeniden boyutlandırabilir. Bu nedenle, kullanıcının çalışma zamanında yerleşik bir denetimi yeniden boyutlandırmasını etkinleştirmek için, denetimin bir kenarına yeniden boyutlandırılması için denetimi yerleştirin ve ardından Bu kapsayıcının aynı tarafına bir Splitter denetimi yerleştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SplitContainer>
- [Nasıl yapılır: Windows Forms’a Denetimleri Yerleştirme](how-to-dock-controls-on-windows-forms.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
