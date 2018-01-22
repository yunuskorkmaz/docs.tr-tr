---
title: "Nasıl yapılır: Windows Formlarında Sekme Sırasını Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de52a4d7784eb4508d5cf5026b394b7b63ecc56e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Nasıl yapılır: Windows Formlarında Sekme Sırasını Ayarlama
Sekme sırası, kullanıcı odak bir denetimden diğerine SEKME tuşuna basarak hareket sırasıdır. Her form kendi sekme sırası vardır. Varsayılan olarak, sekme sırasını denetimleri oluşturulan siparişi ile aynıdır. Sekme sırası numaralandırma sıfır ile başlar.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-the-tab-order-of-a-control"></a>Bir denetim sekme sırasını ayarlamak için  
  
1.  Üzerinde **Görünüm** menüsünde tıklatın **sekme sırası**.  
  
     Bu formdaki sekme sırası seçim modunu etkinleştirir. Bir sayı (temsil eden <xref:System.Windows.Forms.Control.TabIndex%2A> özelliği) her denetim sol üst köşesinde görüntülenir.  
  
2.  Denetimleri sırayla istediğiniz sekme sırası kurmak için tıklatın.  
  
    > [!NOTE]
    >  Sekme sırası içinde denetimin yer değerinden büyük veya 0 değerine eşit herhangi bir değere ayarlanabilir. Çoğaltmaları ortaya çıktığında iki denetimlerinin z sıralamasını değerlendirilir ve üst denetimi için ilk sekmeli. (Z-formun z ekseni [derinliği] boyunca bir form üzerinde denetimleri görsel katmanlarını sırasıdır. Z düzeni hangi denetimlerin önünde diğer denetimleridir belirler.) Z düzeni hakkında daha fazla bilgi için bkz: [Windows Forms katmanlama nesnelerde](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md).  
  
3.  İşiniz bittiğinde tıklatın **sekme sırası** üzerinde **Görünüm** yeniden sekme sırasını modundan çıkmak için menü.  
  
    > [!NOTE]
    >  Odağı alamıyor denetimleri gibi devre dışı bırakılmış ve görünmez denetimler olmadığı bir <xref:System.Windows.Forms.Control.TabIndex%2A> özelliği ve bu sekme sırası dahil değildir. Bir kullanıcı SEKME tuşuna bastığında gibi bu denetimlerin atlanır.  
  
 Alternatif olarak, sekme sırası Özellikler penceresini kullanarak içinde ayarlanabilir <xref:System.Windows.Forms.Control.TabIndex%2A> özelliği. <xref:System.Windows.Forms.Control.TabIndex%2A> Denetimi özelliği belirler sekme sırası nereye konumlandırılır. Varsayılan olarak, çizilmiş ilk kontrolünde bir <xref:System.Windows.Forms.Control.TabIndex%2A> değer 0, ikinci olan bir <xref:System.Windows.Forms.Control.TabIndex%2A> 1 ve benzeri.  
  
 Ayrıca, varsayılan olarak, bir <xref:System.Windows.Forms.GroupBox> denetimi sahip kendi <xref:System.Windows.Forms.Control.TabIndex%2A> bir tamsayı değeri. A <xref:System.Windows.Forms.GroupBox> denetimin kendisini çalışma zamanında odağa sahip olamaz. Bu nedenle, her denetim içinde bir <xref:System.Windows.Forms.GroupBox> kendi ondalık sahip <xref:System.Windows.Forms.Control.TabIndex%2A> .0 ile başlayan değeri. Doğal olarak <xref:System.Windows.Forms.Control.TabIndex%2A> , bir <xref:System.Windows.Forms.GroupBox> denetim artar, içerdiği denetimleri buna uygun olarak arttırılır. Değiştirdiyseniz bir <xref:System.Windows.Forms.Control.TabIndex%2A> 6 ila 5 değer <xref:System.Windows.Forms.Control.TabIndex%2A> kendi grubundaki ilk denetiminin değeri otomatik olarak değiştirir 6.0 ve böyle devam eder.  
  
 Son olarak, herhangi bir formunuzda çok denetimi sekme sırası atlanabilir. Genellikle, sekme sırayla çalıştırma seçer her denetim sekme sırasında tuşuna basarak. Kapatma tarafından <xref:System.Windows.Forms.Control.TabStop%2A> özelliği, formun sekme sırasını geçirilen denetim yapabilir.  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a>Sekme sırasından denetimi kaldırmak için  
  
1.  Denetimin ayarlamak <xref:System.Windows.Forms.Control.TabStop%2A> özelliğine `false` Özellikleri penceresinde.  
  
     Bir denetim <xref:System.Windows.Forms.Control.TabStop%2A> özelliği ayarlanmış `false` SEKME tuşu ile denetimleri arasında geçiş yapma denetimi atlanır olsa da yine sekme sırası içindeki konumunu korur.  
  
    > [!NOTE]
    >  Radyo düğmesi grubunda çalışma zamanında Durdur tek bir sekmesi vardır. Seçilen düğmesini (diğer bir deyişle, düğmesi ile kendi <xref:System.Windows.Forms.RadioButton.Checked%2A> özelliğini `true`) sahip kendi <xref:System.Windows.Forms.Control.TabStop%2A> özelliği otomatik olarak ayarlamak `true`, diğer düğmeleri varken kendi <xref:System.Windows.Forms.Control.TabStop%2A> özelliğini `false`. Gruplama hakkında daha fazla bilgi için <xref:System.Windows.Forms.RadioButton> denetimleri bkz [gruplandırma Windows Forms RadioButton denetimlerini küme işlevi görecek](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/index.md)  
 [Windows Forms’da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [İşleve Göre Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
