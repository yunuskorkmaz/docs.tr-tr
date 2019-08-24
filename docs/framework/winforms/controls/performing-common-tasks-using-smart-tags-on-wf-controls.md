---
title: 'İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 34c14c0afd9632b06947fd72e46ddbda070cfb0f
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015759"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a>İzlenecek yol: Akıllı etiketleri kullanarak ortak görevleri gerçekleştirme

Windows Forms uygulamanız için form ve denetimler oluştururken, defalarca gerçekleştireceğiniz birçok görev vardır. Bunlar, karşılaştığınız yaygın olarak gerçekleştirilen görevlerden bazılarıdır:

- Bir <xref:System.Windows.Forms.TabControl>sekme ekleme veya kaldırma.

- Bir denetimi üst öğesine yerleştirme.

- Bir <xref:System.Windows.Forms.SplitContainer> denetimin yönünü değiştirme.

Geliştirme hızını artırmak için, birçok denetim, tasarım zamanında tek bir hareket halinde gibi genel görevleri gerçekleştirmenize imkan tanıyan, içeriğe duyarlı menüler sunan akıllı etiketler sunar. Bu görevlere *akıllı etiket fiilleri*denir.

Akıllı Etiketler, tasarımcıda ömrü boyunca bir denetim örneğine bağlı kalır ve her zaman kullanılabilir.

## <a name="create-the-project"></a>Projeyi oluşturma

İlk adım projeyi oluşturmak ve formu kurmak olur.

1. Visual Studio 'da, **Smarttagsexörnek**adlı bir Windows tabanlı uygulama projesi oluşturun.

2. **Windows Form Tasarımcısı**formunu seçin.

## <a name="use-smart-tags"></a>Akıllı etiketleri kullanma

Akıllı Etiketler, bunları sunan denetimlerde her zaman tasarım zamanında kullanılabilir.

1. <xref:System.Windows.Forms.TabControl> **Araç kutusundan** bir öğesini formunuza sürükleyin. Öğesinin![tarafındagörüntülenen](./media/vs-winformsmttagglyph.gif)akıllı etiket karakterini (akıllı etiket karakter) unutmayın. <xref:System.Windows.Forms.TabControl>

2. Akıllı etiket glifi ' ne tıklayın. Glifin yanında görünen kısayol menüsünde **sekme öğesi Ekle** öğesini seçin. Yeni bir sekme sayfasının öğesine <xref:System.Windows.Forms.TabControl>eklendiğini gözlemleyin.

3. <xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

4. Akıllı etiket glifi ' ne tıklayın. Glifin yanında görünen kısayol menüsünde, **sütun Ekle** öğesini seçin. <xref:System.Windows.Forms.TableLayoutPanel> Denetime yeni bir sütun eklendiğini gözlemleyin.

5. <xref:System.Windows.Forms.SplitContainer> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

6. Akıllı etiket glifi ' ne tıklayın. Glifin yanında görünen kısayol menüsünde **yatay Bölümlendirici yön** öğesini seçin. <xref:System.Windows.Forms.SplitContainer> Denetimin Bölümlendirici çubuğunun artık yatay olarak yönlendirildiğini gözlemleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
