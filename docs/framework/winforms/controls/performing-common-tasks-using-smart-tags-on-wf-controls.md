---
title: 'İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07fb43a711ae8b1e2e375b17b136c07f35b1cf39
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459580"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a>İzlenecek yol: akıllı etiketleri kullanarak ortak görevleri gerçekleştirme

Windows Forms uygulamanız için form ve denetimler oluştururken, defalarca gerçekleştireceğiniz birçok görev vardır. Bunlar, karşılaştığınız yaygın olarak gerçekleştirilen görevlerden bazılarıdır:

- <xref:System.Windows.Forms.TabControl>sekme ekleme veya kaldırma.

- Bir denetimi üst öğesine yerleştirme.

- <xref:System.Windows.Forms.SplitContainer> denetiminin yönünü değiştirme.

Geliştirme hızını artırmak için, birçok denetim, tasarım zamanında tek bir hareket halinde gibi genel görevleri gerçekleştirmenize imkan tanıyan, içeriğe duyarlı menüler sunan akıllı etiketler sunar. Bu görevlere *akıllı etiket fiilleri*denir.

Akıllı Etiketler, tasarımcıda ömrü boyunca bir denetim örneğine bağlı kalır ve her zaman kullanılabilir.

## <a name="create-the-project"></a>Projeyi oluşturma

İlk adım projeyi oluşturmak ve formu kurmak olur.

1. Visual Studio 'da, **Smarttagsexörnek**adlı bir Windows tabanlı uygulama projesi oluşturun.

2. **Windows Form Tasarımcısı**formunu seçin.

## <a name="use-smart-tags"></a>Akıllı etiketleri kullanma

Akıllı Etiketler, bunları sunan denetimlerde her zaman tasarım zamanında kullanılabilir.

1. **Araç kutusundan** bir <xref:System.Windows.Forms.TabControl> form üzerine sürükleyin. <xref:System.Windows.Forms.TabControl>tarafında görüntülenen akıllı etiket kabartmasını (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif)) unutmayın.

2. Akıllı etiket glifi ' ne tıklayın. Glifin yanında görünen kısayol menüsünde **sekme öğesi Ekle** öğesini seçin. <xref:System.Windows.Forms.TabControl>yeni bir sekme sayfasının eklendiğini gözlemleyin.

3. **Araç kutusundan** bir <xref:System.Windows.Forms.TableLayoutPanel> denetimini formunuza sürükleyin.

4. Akıllı etiket glifi ' ne tıklayın. Glifin yanında görünen kısayol menüsünde, **sütun Ekle** öğesini seçin. <xref:System.Windows.Forms.TableLayoutPanel> denetimine yeni bir sütun eklendiğini gözlemleyin.

5. **Araç kutusundan** bir <xref:System.Windows.Forms.SplitContainer> denetimini formunuza sürükleyin.

6. Akıllı etiket glifi ' ne tıklayın. Glifin yanında görünen kısayol menüsünde **yatay Bölümlendirici yön** öğesini seçin. <xref:System.Windows.Forms.SplitContainer> denetiminin Bölümlendirici çubuğunun artık yatay olarak yönlendirildiğini gözlemleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
