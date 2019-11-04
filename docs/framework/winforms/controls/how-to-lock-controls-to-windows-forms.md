---
title: 'Nasıl yapılır: Windows Formlarına Denetimler Kilitleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d157ddc8be4b5fa0057241b562e76b566e8dad99
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458347"
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
