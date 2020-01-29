---
title: Denetimleri Kilitleme
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 16eb151dc435614e1edc82bf9f0acf3974f36690
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736241"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Nasıl yapılır: Windows Forms denetimleri kilitleme

Windows uygulamanızın kullanıcı arabirimini (UI) tasarladığınızda, denetimleri doğru konumlandırıldıktan sonra kilitleyebilir, böylece diğer özellikleri ayarlarken farkında olmadan taşıyamazsınız veya yeniden boyutlandıramazsınız.

Ayrıca, formdaki tüm denetimleri tek seferde kilitleyebilir ve kilidini açabilir, bu da birçok denetim içeren formlar için faydalıdır veya ayrı denetimlerin kilidini açabilirsiniz. Form üzerinde istediğiniz yere tüm denetimleri yerleştirdikten sonra, hatalı hareketi engellemek için bunları bir yerde kilitleyin.

## <a name="to-lock-a-control"></a>Bir denetimi kilitlemek için

Visual Studio 'nun **Özellikler** penceresinde **kilitli** özelliğini seçin ve ardından **doğru**öğesini seçin. (Adı çift tıklatmak Özellik ayarında geçiş yapar.)

Alternatif olarak, denetimi sağ tıklatın ve **denetimleri kilitle**' yi seçin.

> [!NOTE]
> Denetimleri kilitlemek, bunların tasarım yüzeyinde yeni bir boyuta veya konuma sürüklemesini önler. Ancak, denetimlerin boyutunu veya konumunu **Özellikler** penceresi veya kod içinde de değiştirebilirsiniz.

## <a name="to-lock-all-the-controls-on-a-form"></a>Form üzerindeki tüm denetimleri kilitlemek için

**Biçim** menüsünde, **denetimleri kilitle**' yi seçin.

> [!NOTE]
> Form bir denetim olduğundan, bu komut formun boyutunu da kilitler.

## <a name="to-unlock-all-locked-controls-on-a-form"></a>Form üzerindeki tüm kilitli denetimlerin kilidini açmak için

**Biçim** menüsünde, **denetimleri kilitle**' yi seçin.

Formdaki daha önce kilitlenen tüm denetimlerin kilidi açıldı.

## <a name="to-unlock-locked-controls-individually"></a>Kilitli denetimlerin kilidini ayrı olarak açmak için

**Özellikler** penceresinde **kilitli** özelliğini seçin ve sonra **false**' ı seçin. (Adı çift tıklatmak Özellik ayarında geçiş yapar.)

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
