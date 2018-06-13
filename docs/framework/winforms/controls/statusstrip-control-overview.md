---
title: StatusStrip Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
ms.openlocfilehash: b915be2db6865a95d2d37afda58983dbb2edca27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537914"
---
# <a name="statusstrip-control-overview"></a>StatusStrip Denetimine Genel Bakış
A <xref:System.Windows.Forms.StatusStrip> denetim üzerinde görüntülenen bir nesne hakkındaki bilgileri görüntüler bir <xref:System.Windows.Forms.Form>, nesnenin bileşenleri veya o nesnenin işlemi, uygulamanızda ilgili bağlamsal bilgi. Genellikle, bir <xref:System.Windows.Forms.StatusStrip> denetim oluşur <xref:System.Windows.Forms.ToolStripStatusLabel> nesneleri, metin, simge ya da her ikisini de her biri görüntüler. <xref:System.Windows.Forms.StatusStrip> De içerebilir <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, ve <xref:System.Windows.Forms.ToolStripProgressBar> kontrol eder.  
  
 Varsayılan <xref:System.Windows.Forms.StatusStrip> hiçbir paneller vardır. Bölmeleri eklemek için bir <xref:System.Windows.Forms.StatusStrip>, kullanın <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> yöntemi.  
  
 İşleme için kapsamlı destek <xref:System.Windows.Forms.StatusStrip> öğeleri ve Visual Studio yaygın komutları.  
  
 Ayrıca bkz. [StatusStrip öğeleri koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).  
  
 Ancak <xref:System.Windows.Forms.StatusStrip> değiştirir ve genişletir <xref:System.Windows.Forms.StatusBar> önceki sürümlerinde, denetimin <xref:System.Windows.Forms.StatusBar> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.  
  
### <a name="important-statusstrip-members"></a>Önemli StatusStrip üyeleri  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|Belirten değeri alır veya ayarlar olup olmadığını <xref:System.Windows.Forms.StatusStrip> taşması işlevselliği destekler.|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|Belirten değeri alır veya ayarlar olup olmadığını <xref:System.Windows.Forms.StatusStrip> uzatır uçtan uca içinde kendi <xref:System.Windows.Forms.ToolStripContainer>.|  
  
### <a name="important-statusstrip-companion-classes"></a>Önemli StatusStrip yardımcı sınıfları  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Masası'nda temsil eden bir <xref:System.Windows.Forms.StatusStrip> denetim.|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|İlişkili bir görüntüler <xref:System.Windows.Forms.ToolStripDropDown> alınacağı kullanıcı tek bir öğe seçebilirsiniz.|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|Standart bir düğme ve bir açılır menü iki parçalı bir denetimi temsil eder.|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|Bir işleminin tamamlanma durumunu görüntüler.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
