---
title: 'Nasıl yapılır: UserControl Sınıfından Devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 5e9bdb6d6628b1c696b7944dc0ea1f4c974c8172
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941134"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Nasıl yapılır: UserControl Sınıfından Devralma
Özel kod gerektirmeyen bir veya daha fazla Windows Forms denetimleri işlevlerini birleştirmek için oluşturabileceğiniz bir *kullanıcı denetimi*. Kullanıcı denetimleri hızlı denetimi geliştirme birleştirmek, işlevselliği ve özel özellik ve yöntem çok yönlülük standart Windows Forms denetimi. Bir kullanıcı denetimi oluşturma başladığınızda, standart Windows Forms denetimleri yerleştirebilirsiniz görünür Tasarımcısı ile sunulur. Bu denetimler, tüm iç işlevleri yanı sıra görünümünü ve davranışını (Görünüm) standart denetimler korur. Bu denetimler, kullanıcı denetimine oluşturulur, sonra ancak bunlar artık kod kullanılabilir. Kullanıcı denetimi, kendi boyama yapar ve ayrıca temel işlevleri denetimleriyle ilişkili tüm işler.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-user-control"></a>Bir kullanıcı denetimi oluşturmak için  
  
1. Yeni bir **Windows Denetim Kitaplığı** proje.  
  
     Boş kullanıcı denetimi ile yeni bir Proje oluşturulur.  
  
2. Sürükleyin denetimlerden **Windows Forms** sekmesinde **araç kutusu** , tasarımcıya.  
  
3. Bu denetimler konumlandırılır ve son kullanıcı denetimi görünmesini istediğiniz şekilde tasarlanmıştır. Geliştiricilerin bağlı denetimler erişim izin vermek istiyorsanız, bunları ortak olarak bildirmek veya seçmeli olarak bağlı denetimin özelliklerini göstermek. Ayrıntılar için bkz [nasıl yapılır: Bağlı denetimlerin özelliklerini açığa](how-to-expose-properties-of-constituent-controls.md).  
  
4. Herhangi bir özel yöntemler veya denetiminiz birleştirecektir özellikleri uygulayın.  
  
5. Projeyi oluşturmak ve denetim çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**. Daha fazla bilgi için [nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
- [Nasıl yapılır: Denetim sınıfından devralma](how-to-inherit-from-the-control-class.md)
- [Nasıl yapılır: Mevcut Windows Formları denetimlerinden devralma](how-to-inherit-from-existing-windows-forms-controls.md)
- [Nasıl yapılır: Windows Forms için yazar denetimleri](how-to-author-controls-for-windows-forms.md)
- [Basic'de devralınmış olay işleyicileri Visual Basic sorunlarını giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
