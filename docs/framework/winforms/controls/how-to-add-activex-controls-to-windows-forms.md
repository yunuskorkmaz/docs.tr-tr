---
title: 'Nasıl yapılır: Windows Forms’a ActiveX Denetimleri Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 17311adade187ef3c8e4e639299e6c5cbbcd98a9
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210386"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Nasıl yapılır: Windows Forms’a ActiveX Denetimleri Ekleme

Windows Form Tasarımcısı'nda Visual Studio ana bilgisayar Windows Forms denetimleri için iyileştirilmiştir, ancak Windows Forms ActiveX denetimleri de koyabilirsiniz.

> [!CAUTION]
> ActiveX denetimleri kendilerine eklenen zaman Windows Forms için performans sınırlamalar vardır.

ActiveX denetimleri formunuza eklemeden önce araç kutusuna eklemeniz gerekir. Daha fazla bilgi için [COM bileşenlerini, özelleştirme araç kutusu iletişim kutusunda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).

## <a name="add-an-activex-control-to-your-windows-form"></a>Windows formunuza bir ActiveX denetimi ekleme

ActiveX denetimi Windows formunuza eklemek için araç kutusu denetimi çift tıklayın.

Visual Studio denetim için tüm başvuruları projenize ekler. Windows Forms ActiveX denetimlerinde kullanırken göz önünde bulundurmanız gereken noktalar hakkında daha fazla bilgi için bkz. [bir Windows formunda bir ActiveX denetimi Barındırmayla ilgili konular](considerations-when-hosting-an-activex-control-on-a-windows-form.md).

> [!NOTE]
> Windows Forms ActiveX denetim içeri Aktarıcı (AxImp.exe) ActiveX dinamik bağlantı kitaplıkları içeri aktarma sırasında beklenenden farklı türde olay bağımsız değişkenlerini oluşturur. AxImp.exe tarafından oluşturulan bağımsız değişkenleri aşağıdakine benzer: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` beklenir. Bu tutarsızlığı kod normal çalışmasını engellemez olduğunu unutmayın. Ayrıntılar için bkz [Windows Forms ActiveX denetim içeri Aktarıcı (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [Denetimler ve programlanabilir nesneler çeşitli dillerde ve kitaplıklarda karşılaştırılan](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md)
- [Windows Forms’da Denetimleri Düzenleme](arranging-controls-on-windows-forms.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
