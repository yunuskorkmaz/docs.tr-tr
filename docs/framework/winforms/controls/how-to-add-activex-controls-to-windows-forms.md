---
title: 'Nasıl yapılır: Windows Forms’a ActiveX Denetimleri Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 8c4c6c3f96c49401b032e360314794cc800c0551
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987066"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Nasıl yapılır: Windows Forms’a ActiveX Denetimleri Ekleme

Visual Studio 'daki Windows Form Tasarımcısı Windows Forms denetimleri barındırmak için iyileştirilirken, ActiveX denetimlerini Windows Forms de yerleştirebilirsiniz.

> [!CAUTION]
> ActiveX denetimleri bunlara eklendiğinde Windows Forms için performans sınırlamaları vardır.

Formunuza ActiveX denetimleri eklemeden önce, bunları araç kutusuna eklemeniz gerekir. Daha fazla bilgi için bkz. [com bileşenleri, araç kutusunu özelleştirme Iletişim kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).

## <a name="add-an-activex-control-to-your-windows-form"></a>Windows formunuza ActiveX denetimi ekleme

Windows formunuza ActiveX denetimi eklemek için araç kutusu üzerindeki denetime çift tıklayın.

Visual Studio, tüm başvuruları projenizdeki denetime ekler. Windows Forms üzerinde ActiveX denetimleri kullanırken aklınızda bulundurmanız gerekenler hakkında daha fazla bilgi için bkz. [bir Windows formunda ActiveX denetimi barındırırken dikkat edilecek noktalar](considerations-when-hosting-an-activex-control-on-a-windows-form.md).

> [!NOTE]
> Windows Forms ActiveX denetim Içeri aktarıcı (AxImp. exe), ActiveX dinamik bağlantı kitaplıklarının içe aktarılması işlemini üzerinde beklenenden farklı bir türde olay bağımsız değişkenleri oluşturuyor. Aximp. exe tarafından oluşturulan bağımsız değişkenler aşağıdakine benzerdir: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, ne zaman `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` beklenmektedir. Bu ırdüzenleyen 'in kodun normal şekilde çalışmasını önleyemediğini unutmayın. Ayrıntılar için bkz. [Windows Forms ActiveX denetim Içeri aktarıcı (Aximp. exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [Çeşitli dillerde ve kitaplıklarda karşılaştırılan denetimler ve programlanabilir nesneler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
