---
title: StatusStrip Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
ms.openlocfilehash: f6f2d4b19b7ec91c964c72e3aca85e0253c7cc22
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129720"
---
# <a name="statusstrip-control-overview"></a>StatusStrip Denetimine Genel Bakış
A <xref:System.Windows.Forms.StatusStrip> denetimi, görüntülenmekte olan bir nesneyle ilgili bilgileri görüntüler bir <xref:System.Windows.Forms.Form>, nesnenin bileşenlerini veya nesnenin işlemi uygulamanız içinde ilgili bağlamsal bilgi. Genellikle, bir <xref:System.Windows.Forms.StatusStrip> denetim oluşur <xref:System.Windows.Forms.ToolStripStatusLabel> nesneleri, metin, simge ya da her ikisini de her biri görüntüler. <xref:System.Windows.Forms.StatusStrip> De içerebilir <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, ve <xref:System.Windows.Forms.ToolStripProgressBar> kontrol eder.  
  
 Varsayılan <xref:System.Windows.Forms.StatusStrip> hiçbir bölmeleri vardır. Panellere eklemek için bir <xref:System.Windows.Forms.StatusStrip>, kullanın <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> yöntemi.  
  
 İşleme için kapsamlı destek <xref:System.Windows.Forms.StatusStrip> öğeleri ve Visual Studio'daki sık kullanılan komutlar.  
  
 Ayrıca bkz: [StatusStrip öğeler Koleksiyonu Düzenleyicisi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233631(v=vs.100)) ve [StatusStrip görevleri iletişim kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233642(v=vs.100)).  
  
 Ancak <xref:System.Windows.Forms.StatusStrip> değiştirir ve genişleten <xref:System.Windows.Forms.StatusBar> önceki sürümlerinde, denetimin <xref:System.Windows.Forms.StatusBar> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.  
  
### <a name="important-statusstrip-members"></a>StatusStrip önemli üyeleri  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|Belirten bir değeri alır veya ayarlar olmadığını <xref:System.Windows.Forms.StatusStrip> overflow işlevselliği destekler.|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|Belirten bir değeri alır veya ayarlar olmadığını <xref:System.Windows.Forms.StatusStrip> uzatır uçtan uca içinde kendi <xref:System.Windows.Forms.ToolStripContainer>.|  
  
### <a name="important-statusstrip-companion-classes"></a>Önemli StatusStrip yardımcı sınıfları  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Bir panel içinde temsil eden bir <xref:System.Windows.Forms.StatusStrip> denetimi.|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|İlişkili bir görüntüler <xref:System.Windows.Forms.ToolStripDropDown> içinden kullanıcı tek bir öğe seçebilir.|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|Standart bir düğme ve bir açılan menü iki parçalı bir denetimi temsil eder.|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|Bir işlemi tamamlama durumunu görüntüler.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
