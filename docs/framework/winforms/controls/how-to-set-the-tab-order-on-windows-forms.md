---
title: 'Nasıl yapılır: Windows Forms’da Sekme Sırasını Ayarlama'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8a0a1c76b996f10de0ca963c5d8bdc2325a3f6b6
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987096"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Nasıl yapılır: Windows Forms sekme sırasını ayarlama

Sekme sırası, bir kullanıcının odağı bir denetimden diğerine taşıdıkları sıra sekme tuşuna basılarak yapılır. Her formun kendi sekme sırası vardır. Varsayılan olarak, sekme sırası, denetimleri oluşturduğunuz siparişle aynı olur. Sekme sırası numaralandırması sıfır ile başlar.

## <a name="to-set-the-tab-order-of-a-control"></a>Bir denetimin sekme sırasını ayarlamak için

1. Visual Studio 'da, **Görünüm** menüsünde **sekme sırası**' nı seçin.

   Bu, formda sekme sırası seçim modunu etkinleştirir. Her denetimin sol üst köşesinde <xref:System.Windows.Forms.Control.TabIndex%2A> bir sayı (özelliği temsil eder) görünür.

2. İstediğiniz sekme sırasını oluşturmak için denetimlere sırayla tıklayın.

   > [!NOTE]
   > Sekme sırası içindeki bir denetimin yeri, 0 ' dan büyük veya buna eşit bir değere ayarlanabilir. Yinelemeler gerçekleştiğinde, iki denetimin z sırası değerlendirilir ve üstteki denetim ilk olarak sekmeli olur. (Z düzeni, formun z ekseni [derinlik] üzerinde bulunan denetimlerin görsel katmandır. Z sırası, hangi denetimlerin diğer denetimlerin önünde olduğunu belirler.) Z düzeni hakkında daha fazla bilgi için bkz. [Windows Forms nesneleri katmanlama](how-to-layer-objects-on-windows-forms.md).

3. İşiniz bittiğinde, sekme sırası modundan çıkmak için **Görünüm** menüsünde **sekme sırası** ' nı seçin.

   > [!NOTE]
   > Odağı alamayan ve devre dışı bırakılmış ve görünmeyen denetimlerin yanı sıra, <xref:System.Windows.Forms.Control.TabIndex%2A> özelliği olmayan ve sekme sırasına dahil olmayan denetimler. Bir Kullanıcı Tab tuşuna bastığında, bu denetimler atlanır.

Alternatif olarak, sekme sırası <xref:System.Windows.Forms.Control.TabIndex%2A> özelliği kullanılarak Özellikler penceresi ayarlanabilir. Bir <xref:System.Windows.Forms.Control.TabIndex%2A> denetimin özelliği, sekme düzeninde nerede konumlandığını belirler. Varsayılan olarak, çizilen <xref:System.Windows.Forms.Control.TabIndex%2A> ilk denetimin değeri 0, ikincisi <xref:System.Windows.Forms.Control.TabIndex%2A> 1 ' dir ve bu şekilde devam eder.

Ek olarak, varsayılan olarak bir <xref:System.Windows.Forms.GroupBox> denetim kendi <xref:System.Windows.Forms.Control.TabIndex%2A> değerine sahiptir ve bu bir tam sayıdır. Bir <xref:System.Windows.Forms.GroupBox> denetimin kendisi çalışma zamanında odağa sahip olamaz. Bu nedenle, içindeki <xref:System.Windows.Forms.GroupBox> her denetim kendi ondalık <xref:System.Windows.Forms.Control.TabIndex%2A> değerine sahiptir. 0 ile başlar. Doğal olarak, bir <xref:System.Windows.Forms.Control.TabIndex%2A> <xref:System.Windows.Forms.GroupBox> denetimin artdıkça, içindeki denetimler buna göre arttırılır. <xref:System.Windows.Forms.Control.TabIndex%2A> 5<xref:System.Windows.Forms.Control.TabIndex%2A> ' ten 6 ' a bir değer değiştirdiyseniz, grubundaki ilk denetimin değeri otomatik olarak 6,0 olarak değişir ve bu şekilde devam eder.

Son olarak, formunuzda çok sayıda denetim, sekme sırasına göre atlanabilir. Genellikle, çalışma zamanında Tab 'ın her zaman başarılı olarak basılması, sekme düzeninde her bir denetimi seçer. <xref:System.Windows.Forms.Control.TabStop%2A> Özelliği kapatarak, formun sekme düzeninde bir denetimin geçirilmesini sağlayabilirsiniz.

## <a name="to-remove-a-control-from-the-tab-order"></a>Sekme sırasına göre bir denetimi kaldırmak için

<xref:System.Windows.Forms.Control.TabStop%2A> **Özellikler** penceresinde denetimin özelliğini **false** olarak ayarlayın.

Özelliği Tab tuşu <xref:System.Windows.Forms.Control.TabStop%2A> ile denetimlerde geçiş yaptığınızda denetim `false` atlansa bile, özelliği sekme düzeninde hala devam edecek şekilde ayarlanmış olan bir denetim.

> [!NOTE]
> Radyo düğmesi grubunun çalışma zamanında tek bir sekme durağı vardır. Seçili düğme ( <xref:System.Windows.Forms.RadioButton.Checked%2A> diğer bir deyişle, özelliği olarak `true`ayarlanmış olan düğme) <xref:System.Windows.Forms.Control.TabStop%2A> özelliği olarak olarak `true`ayarlanır, diğer düğmelerin <xref:System.Windows.Forms.Control.TabStop%2A> özelliği olarak ayarlanır `false`. Gruplandırma <xref:System.Windows.Forms.RadioButton> denetimleri hakkında daha fazla bilgi için bkz. [bir küme olarak işlev yapmak için Windows Forms RadioButton denetimlerini gruplandırma](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
