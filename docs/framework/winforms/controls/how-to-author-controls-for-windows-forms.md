---
title: 'Nasıl yapılır: Windows Forms için yazar denetimleri'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
ms.openlocfilehash: a6ea57dda8f034684e8590ce4c3b6d37ab01230e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579530"
---
# <a name="how-to-author-controls-for-windows-forms"></a>Nasıl yapılır: Windows Forms için yazar denetimleri
Bir denetimin kullanıcı ve program arasındaki grafik bağlantısını temsil eder. Bir denetim sağlamak veya verileri işlemek, kullanıcı girişi kabul edebilir, olaylara yanıt vermesi veya herhangi bir sayıda kullanıcı ve uygulama bağlanma diğer işlevlerini gerçekleştirmek. Bir denetimi bir bileşen aslında bir grafik arabirimine sahip olduğundan, bir bileşen mu, yanı sıra kullanıcı etkileşimi sağlamak herhangi bir işlevini hizmet verebilir. Denetimler belirli bir amaca hizmet eder oluşturulur ve denetimleri yazma başka bir programlama görevdir. Aklınızda yazma işleminin hızlandırılmasının denetimine genel bakış aşağıdaki adımları temsil eder. Bağlantılar tek tek adımlara ek bilgi sağlar.  
  
> [!NOTE]
>  Web formlarında kullanmak üzere özel bir denetim yazmak istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-author-a-control"></a>Bir denetim yazma  
  
1.  Denetim gerçekleştirmek istediğiniz veya bu kısım belirlemek uygulamanızda yürütülür. Dikkate alınması gereken faktörler şunlardır:  
  
    -   Ne tür bir grafik arabirim ihtiyacınız var?  
  
    -   Bu denetimin hangi belirli kullanıcı etkileşimlerine kullanacak mı?  
  
    -   İhtiyacınız olan işlevleri, mevcut tüm denetimler tarafından sağlanır?  
  
    -   Çeşitli Windows Forms denetimleri bir araya getirerek ihtiyacınız olan işlevleri alabilir miyim?  
  
2.  Denetim için nesne modeli gerekiyorsa, nasıl işlevselliği nesne modeli dağıtılan ve işlevselliği denetim ve tüm alt nesnelerinin arasında yukarı bölmek belirler. Bir nesne modeli, karmaşık bir denetimi planlama veya çeşitli işlevler dahil etmek istiyorsanız yararlı olabilir.  
  
3.  Tür belirleme (örneğin, kullanıcı denetimi, özel denetimi, devralınan Windows Forms denetimi) denetimin ihtiyacınız. Ayrıntılar için bkz [denetim türü önerileri](../../../../docs/framework/winforms/controls/control-type-recommendations.md) ve [özel denetim çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
4.  Özellikleri, yöntemleri ve olayları denetimin ve alt nesnelerinin veya paketinizle yapıları işlevleri hızlı ve uygun erişim düzeyleri (örneğin, genel, korumalı vb.) atayın.  
  
5.  Özel boyama denetim için gerekiyorsa, bunun için kodu ekleyin. Ayrıntılar için bkz [özel denetim boyama ve işleme](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
6.  Denetiminiz öğesinden devralıyorsa <xref:System.Windows.Forms.UserControl>, Denetim projesinin derlenmesi ve çalışır durumda çalışma zamanı davranışını sınama **UserControl Test kapsayıcısı**. Daha fazla bilgi için [nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
7.  Ayrıca, test edin ve bir Windows uygulaması gibi yeni bir proje oluşturma, bir kapsayıcının içine yerleştirerek, denetiminde hata ayıklama. Bu işlemin bir parçası olarak gösterilen [izlenecek yol: Visual Basic ile bileşik denetim yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md).  
  
8.  Her bir özelliği eklemek gibi özellikleri yeni işlevselliği kullanmak için test projenize ekler.  
  
9. Tasarım iyileştirme yineleyin.  
  
10. Paketleme ve denetim dağıtma. Ayrıntılar için bkz [uygulamaları dağıtma, hizmetleri ve bileşenleri](https://msdn.microsoft.com/library/wtzawcsz).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Visual Basic ile bileşik denetim yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [İzlenecek yol: Visual Basic ile Windows Forms Denetimi'nden devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [Nasıl yapılır: UserControl sınıfından devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)
- [Nasıl yapılır: Denetim sınıfından devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)
- [Nasıl yapılır: Mevcut Windows Formları denetimlerinden devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)
- [Nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
