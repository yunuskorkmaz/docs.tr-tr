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
ms.openlocfilehash: d504ace9e5571246ae0e78e165a7ad2bc23fa481
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085304"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme
Geliştirin ve denetimleri dağıtmak gibi bu denetimlerin görünmesini isteyebilirsiniz **araç kutusu öğelerini Seç** , sağ tıkladığınızda görüntülenen iletişim kutusunda, **araç kutusu** seçip  **Öğeleri seçmek**. Denetiminiz AssemblyFoldersEx kayıt yordamı kullanarak bu iletişim kutusunda görüntülenecek etkinleştirebilirsiniz.  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>Denetiminiz araç kutusu öğelerini Seç iletişim kutusunda görüntülemek için  
  
-   Denetim derlemeyi genel derleme önbelleğine yükleyin. Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi genel derleme önbelleğine yükleme](../../app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     -veya-  
  
-   Denetim ve onun ilişkili tasarım zamanı derlemeleri AssemblyFoldersEx kayıt yordamı kullanarak kaydedin. AssemblyFoldersEx, üçüncü taraf satıcılarla destekledikleri framework'ün her sürümü için yollar depoladığınız bir kayıt defteri konumdur. Tasarım zamanı çözümleme başvuru derlemelerini bulmak için bu kayıt defteri konumuna bakabilirsiniz. Kayıt betiği denetimleri araç kutusunda görünmesini istediğiniz belirtebilirsiniz. Daha fazla bilgi için [bir özel denetim ve tasarım zamanı derlemeleri dağıtma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araç kutusu öğelerini Seç iletişim kutusu (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))
- [Özel bir denetim ve tasarım zamanı derlemeleri dağıtma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))
- [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](developing-windows-forms-controls-at-design-time.md)
- [Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğine Yükleme](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
