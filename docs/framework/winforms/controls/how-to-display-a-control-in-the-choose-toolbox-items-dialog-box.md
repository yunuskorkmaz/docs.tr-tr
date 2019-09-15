---
title: 'Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme'
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f52c1d127df8f0e831db0749e3453bb1c54d5886
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972064"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme

Denetimleri geliştirip dağıtırken, **araç** kutusunu sağ tıklayıp **öğeleri seç**' i seçtiğinizde görüntülenen Visual Studio 'Nun **araç kutusu öğelerini Seç** iletişim kutusunda bu denetimlerin görünmesini isteyebilirsiniz. AssemblyFoldersEx kayıt yordamını kullanarak denetiminizin bu iletişim kutusunda görünmesini sağlayabilirsiniz.

Denetiminizi araç kutusu öğelerini Seç iletişim kutusunda göstermek için:

- Denetim derlemenizi genel bütünleştirilmiş kod önbelleğine yükler. Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler](../../app-domains/install-assembly-into-gac.md)

  -veya-

- AssemblyFoldersEx kayıt yordamını kullanarak denetiminizi ve onunla ilişkili tasarım zamanı derlemelerini kaydedin. AssemblyFoldersEx, üçüncü taraf satıcıların destekledikleri her bir sürüm için yolları depolayacağı bir kayıt defteri konumudur. Tasarım zamanı çözümlemesi, başvuru derlemelerini bulmak için bu kayıt defteri konumuna bakabilir. Kayıt defteri betiği, araç kutusunda görünmesini istediğiniz denetimleri belirtebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](developing-windows-forms-controls-at-design-time.md)
- [Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler](../../app-domains/install-assembly-into-gac.md)
- [İzlenecek yol: Araç kutusunu özel bileşenlerle otomatik olarak doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
