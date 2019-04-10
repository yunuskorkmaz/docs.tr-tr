---
title: 'Nasıl yapılır: Windows Forms için Denetimler Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
ms.openlocfilehash: 844d165cef05e46d25960f113af3bf99dd35e14f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340340"
---
# <a name="how-to-author-controls-for-windows-forms"></a>Nasıl yapılır: Windows Forms için Denetimler Yazma
Bir denetimin kullanıcı ve program arasındaki grafik bağlantısını temsil eder. Bir denetim sağlamak veya verileri işlemek, kullanıcı girişi kabul edebilir, olaylara yanıt vermesi veya herhangi bir sayıda kullanıcı ve uygulama bağlanma diğer işlevlerini gerçekleştirmek. Bir denetimi bir bileşen aslında bir grafik arabirimine sahip olduğundan, bir bileşen mu, yanı sıra kullanıcı etkileşimi sağlamak herhangi bir işlevini hizmet verebilir. Denetimler belirli bir amaca hizmet eder oluşturulur ve denetimleri yazma başka bir programlama görevdir. Aklınızda yazma işleminin hızlandırılmasının denetimine genel bakış aşağıdaki adımları temsil eder. Bağlantılar tek tek adımlara ek bilgi sağlar.  
  
> [!NOTE]
>  Web formlarında kullanmak üzere özel bir denetim yazmak istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
>   
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-author-a-control"></a>Bir denetim yazma  
  
1. Denetim gerçekleştirmek istediğiniz veya bu kısım belirlemek uygulamanızda yürütülür. Dikkate alınması gereken faktörler şunlardır:  
  
    -   Ne tür bir grafik arabirim ihtiyacınız var?  
  
    -   Bu denetimin hangi belirli kullanıcı etkileşimlerine kullanacak mı?  
  
    -   İhtiyacınız olan işlevleri, mevcut tüm denetimler tarafından sağlanır?  
  
    -   Çeşitli Windows Forms denetimleri bir araya getirerek ihtiyacınız olan işlevleri alabilir miyim?  
  
2. Denetim için nesne modeli gerekiyorsa, nasıl işlevselliği nesne modeli dağıtılan ve işlevselliği denetim ve tüm alt nesnelerinin arasında yukarı bölmek belirler. Bir nesne modeli, karmaşık bir denetimi planlama veya çeşitli işlevler dahil etmek istiyorsanız yararlı olabilir.  
  
3. Tür belirleme (örneğin, kullanıcı denetimi, özel denetimi, devralınan Windows Forms denetimi) denetimin ihtiyacınız. Ayrıntılar için bkz [denetim türü önerileri](control-type-recommendations.md) ve [özel denetim çeşitleri](varieties-of-custom-controls.md).  
  
4. Özellikleri, yöntemleri ve olayları denetimin ve alt nesnelerinin veya paketinizle yapıları işlevleri hızlı ve uygun erişim düzeyleri (örneğin, genel, korumalı vb.) atayın.  
  
5. Özel boyama denetim için gerekiyorsa, bunun için kodu ekleyin. Ayrıntılar için bkz [özel denetim boyama ve işleme](custom-control-painting-and-rendering.md).  
  
6. Denetiminiz öğesinden devralıyorsa <xref:System.Windows.Forms.UserControl>, Denetim projesinin derlenmesi ve çalışır durumda çalışma zamanı davranışını sınama **UserControl Test kapsayıcısı**. Daha fazla bilgi için [nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
7. Ayrıca, test edin ve bir Windows uygulaması gibi yeni bir proje oluşturma, bir kapsayıcının içine yerleştirerek, denetiminde hata ayıklama. Bu işlemin bir parçası olarak gösterilen [izlenecek yol: Visual Basic ile bileşik denetim yazma](walkthrough-authoring-a-composite-control-with-visual-basic.md).  
  
8. Her bir özelliği eklemek gibi özellikleri yeni işlevselliği kullanmak için test projenize ekler.  
  
9. Tasarım iyileştirme yineleyin.  
  
10. Paketleme ve denetim dağıtma. Ayrıntılar için bkz [Visual Studio'daki dağıtımı da ilk bakmak](/visualstudio/deployment/deploying-applications-services-and-components).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Visual Basic İle Bileşik Denetim Yazma](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [Nasıl yapılır: UserControl Sınıfından Devralma](how-to-inherit-from-the-usercontrol-class.md)
- [Nasıl yapılır: Control Sınıfından Devralma](how-to-inherit-from-the-control-class.md)
- [Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma](how-to-inherit-from-existing-windows-forms-controls.md)
- [Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
