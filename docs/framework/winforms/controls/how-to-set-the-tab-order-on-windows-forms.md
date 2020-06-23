---
title: Denetimlerin sekme sırasını ayarla
description: Windows Forms denetimlerin sekme sırasını ayarlamayı öğrenin. Sekme sırasını Visual Studio ile ayarlayın veya Özellikler penceresi TabIndex özelliğini kullanın.
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
ms.openlocfilehash: 3d16da1ac73cc030b92bb36c4bfa3a79985339bf
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903369"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Nasıl yapılır: Windows Forms sekme sırasını ayarlama

Sekme sırası, bir kullanıcının odağı bir denetimden diğerine taşıdıkları sıra sekme tuşuna basılarak yapılır. Her formun kendi sekme sırası vardır. Varsayılan olarak, sekme sırası, denetimleri oluşturduğunuz siparişle aynı olur. Sekme sırası numaralandırması sıfır ile başlar.

## <a name="to-set-the-tab-order-of-a-control"></a>Bir denetimin sekme sırasını ayarlamak için

1. Visual Studio 'da, **Görünüm** menüsünde **sekme sırası**' nı seçin.

   Bu, formda sekme sırası seçim modunu etkinleştirir. <xref:System.Windows.Forms.Control.TabIndex%2A>Her denetimin sol üst köşesinde bir sayı (özelliği temsil eder) görünür.

2. İstediğiniz sekme sırasını oluşturmak için denetimlere sırayla tıklayın.

   > [!NOTE]
   > Sekme sırası içindeki bir denetimin yeri, 0 ' dan büyük veya buna eşit bir değere ayarlanabilir. Yinelemeler gerçekleştiğinde, iki denetimin z sırası değerlendirilir ve üstteki denetim ilk olarak sekmeli olur. (Z düzeni, formun z ekseni [derinlik] üzerinde bulunan denetimlerin görsel katmandır. Z sırası, hangi denetimlerin diğer denetimlerin önünde olduğunu belirler.) Z düzeni hakkında daha fazla bilgi için bkz. [Windows Forms nesneleri katmanlama](how-to-layer-objects-on-windows-forms.md).

3. İşiniz bittiğinde, sekme sırası modundan çıkmak için **Görünüm** menüsünde **sekme sırası** ' nı seçin.

   > [!NOTE]
   > Odağı alamayan ve devre dışı bırakılmış ve görünmeyen denetimlerin yanı <xref:System.Windows.Forms.Control.TabIndex%2A> sıra, özelliği olmayan ve sekme sırasına dahil olmayan denetimler. Bir Kullanıcı Tab tuşuna bastığında, bu denetimler atlanır.

Alternatif olarak, sekme sırası özelliği kullanılarak Özellikler penceresi ayarlanabilir <xref:System.Windows.Forms.Control.TabIndex%2A> . <xref:System.Windows.Forms.Control.TabIndex%2A>Bir denetimin özelliği, sekme düzeninde nerede konumlandığını belirler. Varsayılan olarak, çizilen ilk denetimin <xref:System.Windows.Forms.Control.TabIndex%2A> değeri 0, ikincisi <xref:System.Windows.Forms.Control.TabIndex%2A> 1 ' dir ve bu şekilde devam eder.

Ek olarak, varsayılan olarak bir <xref:System.Windows.Forms.GroupBox> Denetim kendi değerine sahiptir <xref:System.Windows.Forms.Control.TabIndex%2A> ve bu bir tam sayıdır. Bir <xref:System.Windows.Forms.GroupBox> denetimin kendisi çalışma zamanında odağa sahip olamaz. Bu nedenle, içindeki her denetim <xref:System.Windows.Forms.GroupBox> kendi ondalık değerine sahiptir <xref:System.Windows.Forms.Control.TabIndex%2A> . 0 ile başlar. Doğal olarak, <xref:System.Windows.Forms.Control.TabIndex%2A> bir <xref:System.Windows.Forms.GroupBox> denetimin artdıkça, içindeki denetimler buna göre arttırılır. <xref:System.Windows.Forms.Control.TabIndex%2A>5 ' ten 6 ' a bir değer değiştirdiyseniz, <xref:System.Windows.Forms.Control.TabIndex%2A> grubundaki ilk denetimin değeri otomatik olarak 6,0 olarak değişir ve bu şekilde devam eder.

Son olarak, formunuzda çok sayıda denetim, sekme sırasına göre atlanabilir. Genellikle, çalışma zamanında Tab 'ın her zaman başarılı olarak basılması, sekme düzeninde her bir denetimi seçer. <xref:System.Windows.Forms.Control.TabStop%2A>Özelliği kapatarak, formun sekme düzeninde bir denetimin geçirilmesini sağlayabilirsiniz.

## <a name="to-remove-a-control-from-the-tab-order"></a>Sekme sırasına göre bir denetimi kaldırmak için

<xref:System.Windows.Forms.Control.TabStop%2A> **Özellikler** penceresinde denetimin özelliğini **false** olarak ayarlayın.

<xref:System.Windows.Forms.Control.TabStop%2A>Özelliği `false` Tab tuşu ile denetimlerde geçiş yaptığınızda denetim atlansa bile, özelliği sekme düzeninde hala devam edecek şekilde ayarlanmış olan bir denetim.

> [!NOTE]
> Radyo düğmesi grubunun çalışma zamanında tek bir sekme durağı vardır. Seçili düğme (diğer bir deyişle, özelliği olarak ayarlanmış olan düğme <xref:System.Windows.Forms.RadioButton.Checked%2A> `true` ) <xref:System.Windows.Forms.Control.TabStop%2A> özelliği olarak olarak ayarlanır `true` , diğer düğmelerin <xref:System.Windows.Forms.Control.TabStop%2A> özelliği olarak ayarlanır `false` . Gruplandırma denetimleri hakkında daha fazla bilgi için <xref:System.Windows.Forms.RadioButton> bkz. [bir küme olarak işlev yapmak Için Windows Forms RadioButton denetimlerini gruplandırma](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms denetimleri](index.md)
- [Windows Forms'ta Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
