---
title: 'Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme'
ms.date: 03/30/2017
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
ms.openlocfilehash: 9a6938b4fe651e13f3ec96642db6027143f1f028
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015890"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme

Denetimleri geliştirip dağıtırken, **araç** kutusunu sağ tıklayıp **öğeleri seç**' i seçtiğinizde görüntülenen Visual Studio 'Nun **araç kutusu öğelerini Seç** iletişim kutusunda bu denetimlerin görünmesini isteyebilirsiniz. AssemblyFoldersEx kayıt yordamını kullanarak denetiminizin bu iletişim kutusunda görünmesini sağlayabilirsiniz.

Denetiminizi araç kutusu öğelerini Seç iletişim kutusunda göstermek için:

- Denetim derlemenizi genel bütünleştirilmiş kod önbelleğine yükler. Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler](../../app-domains/how-to-install-an-assembly-into-the-gac.md)

  -veya-

- AssemblyFoldersEx kayıt yordamını kullanarak denetiminizi ve onunla ilişkili tasarım zamanı derlemelerini kaydedin. AssemblyFoldersEx, üçüncü taraf satıcıların destekledikleri her bir sürüm için yolları depolayacağı bir kayıt defteri konumudur. Tasarım zamanı çözümlemesi, başvuru derlemelerini bulmak için bu kayıt defteri konumuna bakabilir. Kayıt defteri betiği, araç kutusunda görünmesini istediğiniz denetimleri belirtebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](developing-windows-forms-controls-at-design-time.md)
- [Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [İzlenecek yol: Araç kutusunu özel bileşenlerle otomatik olarak doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
