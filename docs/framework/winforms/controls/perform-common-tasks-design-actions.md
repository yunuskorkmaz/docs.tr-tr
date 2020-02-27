---
title: Denetimlerde tasarımcı eylemlerini kullanarak ortak görevleri gerçekleştirme
ms.date: 02/13/2019
helpviewer_keywords:
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 342741b9ce032b1b8ec50a6c689d9109d12f5b3b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634885"
---
# <a name="walkthrough-perform-common-tasks-using-designer-actions"></a>İzlenecek yol: tasarımcı eylemlerini kullanarak ortak görevleri gerçekleştirme

Windows Forms uygulamanız için form ve denetimler oluştururken, defalarca gerçekleştireceğiniz birçok görev vardır. Aşağıdaki listede, tüm sık gerçekleştirilen görevlerden bazıları gösterilir:

- <xref:System.Windows.Forms.TabControl>sekme ekleme veya kaldırma.
- Bir denetimi üst öğesine yerleştirme.
- <xref:System.Windows.Forms.SplitContainer> denetiminin yönünü değiştirme.

Geliştirme hızını artırmak için birçok denetim Tasarımcı eylemleri sunar; bu, tasarım zamanında tek bir hareket halinde gibi genel görevleri gerçekleştirmenize olanak tanıyan içeriğe duyarlı menüler sağlar. Bu görevlere *Tasarımcı eylemleri fiilleri*denir.

Tasarımcı eylemleri, tasarımcıda ömrü boyunca bir denetim örneğine bağlı kalır ve her zaman kullanılabilir.

## <a name="create-the-project"></a>Proje oluşturma

İlk adım projeyi oluşturmak ve formu kurmak olur.

1. Visual Studio 'da **Designeractionsexörnek**adlı bir Windows tabanlı uygulama projesi oluşturun.

2. **Windows Form Tasarımcısı**formunu seçin.

## <a name="use-designer-actions"></a>Tasarımcı eylemlerini kullanma

Tasarımcı eylemleri, bunları sunan denetimlerde her zaman tasarım zamanında kullanılabilir.

1. **Araç kutusundan** bir <xref:System.Windows.Forms.TabControl> form üzerine sürükleyin. <xref:System.Windows.Forms.TabControl>tarafında görüntülenen tasarımcı eylemleri glifin (![küçük siyah ok](./media/designer-actions-glyph.gif)) not edin.

2. Tasarımcı eylemleri glifi ' ne tıklayın. Glifin yanında görünen kısayol menüsünde **sekme öğesi Ekle** öğesini seçin. <xref:System.Windows.Forms.TabControl>yeni bir sekme sayfasının eklendiğini gözlemleyin.

3. **Araç kutusundan** bir <xref:System.Windows.Forms.TableLayoutPanel> denetimini formunuza sürükleyin.

4. Tasarımcı eylemleri glifi ' ne tıklayın. Glifin yanında görünen kısayol menüsünde, **sütun Ekle** öğesini seçin. <xref:System.Windows.Forms.TableLayoutPanel> denetimine yeni bir sütun eklendiğini gözlemleyin.

5. **Araç kutusundan** bir <xref:System.Windows.Forms.SplitContainer> denetimini formunuza sürükleyin.

6. Tasarımcı eylemleri glifi ' ne tıklayın. Glifin yanında görünen kısayol menüsünde **yatay Bölümlendirici yön** öğesini seçin. <xref:System.Windows.Forms.SplitContainer> denetiminin Bölümlendirici çubuğunun artık yatay olarak yönlendirildiğini gözlemleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
