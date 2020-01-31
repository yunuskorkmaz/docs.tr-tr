---
title: Denetimlerin sekme sırasını ayarla
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5d53e411bda0279271e4f73e1842c52fd6d9b3a9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746833"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Nasıl yapılır: Windows Forms sekme sırasını ayarlama

Sekme sırası, bir kullanıcının odağı bir denetimden diğerine taşıdıkları sıra sekme tuşuna basılarak yapılır. Her formun kendi sekme sırası vardır. Varsayılan olarak, sekme sırası, denetimleri oluşturduğunuz siparişle aynı olur. Sekme sırası numaralandırması sıfır ile başlar.

## <a name="to-set-the-tab-order-of-a-control"></a>Bir denetimin sekme sırasını ayarlamak için

1. Visual Studio 'da, **Görünüm** menüsünde **sekme sırası**' nı seçin.

   Bu, formda sekme sırası seçim modunu etkinleştirir. Her denetimin sol üst köşesinde bir sayı (<xref:System.Windows.Forms.Control.TabIndex%2A> özelliğini temsil) görüntülenir.

2. İstediğiniz sekme sırasını oluşturmak için denetimlere sırayla tıklayın.

   > [!NOTE]
   > Sekme sırası içindeki bir denetimin yeri, 0 ' dan büyük veya buna eşit bir değere ayarlanabilir. Yinelemeler gerçekleştiğinde, iki denetimin z sırası değerlendirilir ve üstteki denetim ilk olarak sekmeli olur. (Z düzeni, formun z ekseni [derinlik] üzerinde bulunan denetimlerin görsel katmandır. Z sırası, hangi denetimlerin diğer denetimlerin önünde olduğunu belirler.) Z düzeni hakkında daha fazla bilgi için bkz. [Windows Forms nesneleri katmanlama](how-to-layer-objects-on-windows-forms.md).

3. İşiniz bittiğinde, sekme sırası modundan çıkmak için **Görünüm** menüsünde **sekme sırası** ' nı seçin.

   > [!NOTE]
   > Devre dışı bırakılmış ve görünmeyen denetimlerin yanı sıra, odağı alamayan denetimlerin <xref:System.Windows.Forms.Control.TabIndex%2A> bir özelliği yoktur ve sekme sırasına dahil edilmez. Bir Kullanıcı Tab tuşuna bastığında, bu denetimler atlanır.

Alternatif olarak, sekme sırası <xref:System.Windows.Forms.Control.TabIndex%2A> özelliğini kullanarak Özellikler penceresi ayarlanabilir. Bir denetimin <xref:System.Windows.Forms.Control.TabIndex%2A> özelliği, sekme düzeninde nerede konumlandığını belirler. Varsayılan olarak, çizilen ilk denetimin değeri 0 <xref:System.Windows.Forms.Control.TabIndex%2A>, ikincisi ise 1 <xref:System.Windows.Forms.Control.TabIndex%2A> ve bu şekilde devam eder.

Ayrıca, varsayılan olarak, bir <xref:System.Windows.Forms.GroupBox> denetimi bir tam sayı olan kendi <xref:System.Windows.Forms.Control.TabIndex%2A> değerine sahiptir. <xref:System.Windows.Forms.GroupBox> denetiminin kendisi çalışma zamanında odağa sahip olamaz. Bu nedenle, bir <xref:System.Windows.Forms.GroupBox> içindeki her denetim,. 0 ' dan başlayan kendi ondalık <xref:System.Windows.Forms.Control.TabIndex%2A> değerine sahiptir. Doğal olarak, bir <xref:System.Windows.Forms.GroupBox> denetiminin <xref:System.Windows.Forms.Control.TabIndex%2A> artdıkça, içindeki denetimler buna göre arttırılır. 5 ' ten 6 ' a <xref:System.Windows.Forms.Control.TabIndex%2A> bir değeri değiştirdiyseniz, grubundaki ilk denetimin <xref:System.Windows.Forms.Control.TabIndex%2A> değeri otomatik olarak 6,0 olarak değişir ve bu şekilde devam eder.

Son olarak, formunuzda çok sayıda denetim, sekme sırasına göre atlanabilir. Genellikle, çalışma zamanında Tab 'ın her zaman başarılı olarak basılması, sekme düzeninde her bir denetimi seçer. <xref:System.Windows.Forms.Control.TabStop%2A> özelliğini kapatarak, formun sekme düzeninde bir denetimin geçirilmesini sağlayabilirsiniz.

## <a name="to-remove-a-control-from-the-tab-order"></a>Sekme sırasına göre bir denetimi kaldırmak için

**Özellikler** penceresinde denetimin <xref:System.Windows.Forms.Control.TabStop%2A> özelliğini **false** olarak ayarlayın.

<xref:System.Windows.Forms.Control.TabStop%2A> özelliği, Tab tuşu ile denetimlerde geçiş yaptığınızda denetim atlansa bile, `false` olarak ayarlanmış bir denetim, sekme düzeninde hala konumunu korur.

> [!NOTE]
> Radyo düğmesi grubunun çalışma zamanında tek bir sekme durağı vardır. Seçilen düğme (diğer bir deyişle, <xref:System.Windows.Forms.RadioButton.Checked%2A> özelliği `true`olarak ayarlanan düğmenin <xref:System.Windows.Forms.Control.TabStop%2A> özelliği otomatik olarak `true`olarak ayarlanır, diğer düğmelerin <xref:System.Windows.Forms.Control.TabStop%2A> özelliği `false`olarak ayarlanmıştır. Gruplandırma <xref:System.Windows.Forms.RadioButton> denetimleri hakkında daha fazla bilgi için, bkz. [küme olarak işlev yapmak için Windows Forms RadioButton denetimlerini gruplandırma](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
