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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db4b3ac020e967a6a0c291103d825ac71cebda23
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458274"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme

Denetimleri geliştirip dağıtırken, **araç** kutusunu sağ tıklayıp **öğeleri seç**' i seçtiğinizde görüntülenen Visual Studio 'Nun **araç kutusu öğelerini Seç** iletişim kutusunda bu denetimlerin görünmesini isteyebilirsiniz. AssemblyFoldersEx kayıt yordamını kullanarak denetiminizin bu iletişim kutusunda görünmesini sağlayabilirsiniz.

Denetiminizi araç kutusu öğelerini Seç iletişim kutusunda göstermek için:

- Denetim derlemenizi genel bütünleştirilmiş kod önbelleğine yükler. Daha fazla bilgi için bkz. [nasıl yapılır: bir derlemeyi genel derleme önbelleğine yüklemek](../../app-domains/install-assembly-into-gac.md).

  veya

- AssemblyFoldersEx kayıt yordamını kullanarak denetiminizi ve onunla ilişkili tasarım zamanı derlemelerini kaydedin. AssemblyFoldersEx, üçüncü taraf satıcıların destekledikleri her bir sürüm için yolları depolayacağı bir kayıt defteri konumudur. Tasarım zamanı çözümlemesi, başvuru derlemelerini bulmak için bu kayıt defteri konumuna bakabilir. Kayıt defteri betiği, araç kutusunda görünmesini istediğiniz denetimleri belirtebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](developing-windows-forms-controls-at-design-time.md)
- [Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğine Yükleme](../../app-domains/install-assembly-into-gac.md)
- [İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
