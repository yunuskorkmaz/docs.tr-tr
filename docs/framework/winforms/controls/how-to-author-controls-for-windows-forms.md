---
title: 'Nasıl yapılır: Windows Forms için Denetimler Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 45a6ae68102204ad8506027065c2676e02fdd7a3
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015913"
---
# <a name="how-to-author-controls-for-windows-forms"></a>Nasıl yapılır: Windows Forms için yazar denetimleri

Denetim, Kullanıcı ve program arasındaki grafik bağlantısını temsil eder. Bir denetim, verileri sağlayabilir veya işleyebilir, Kullanıcı girişi kabul edebilir, olaylara yanıt verebilir veya Kullanıcı ve uygulamayı bağlayan herhangi bir sayıda diğer işlevi gerçekleştirebilir. Bir denetim temelde grafik arabirimi olan bir bileşen olduğundan, bir bileşenin yaptığı ve Kullanıcı etkileşimi sağlayan herhangi bir işleve de sahip olabilir. Denetimler, belirli amaçlarla kullanılmak üzere oluşturulur ve yazma denetimleri yalnızca başka bir programlama görevi olur. Bu şekilde, aşağıdaki adımlar denetim yazma sürecine genel bir bakış temsil eder. Bağlantılar, bireysel adımlarla ilgili ek bilgi sağlar.

## <a name="to-author-a-control"></a>Bir denetimi yazmak için

1. Denetiminizin ne yapmak istediğinizi veya uygulamanızda hangi parçayı oynaymasını istediğinizi saptayın. Göz önünde bulundurulması gereken etkenler şunlardır:

    - Ne tür bir grafik arabirimine ihtiyacınız var?

    - Bu denetim hangi kullanıcı etkileşimlerini işleyecek?

    - Var olan tüm denetimler için gerekli olan işlevsellikdir?

    - Birkaç Windows Forms denetimini birleştirerek ihtiyacınız olan işlevleri alabilir misiniz?

2. Denetiminiz için bir nesne modeline ihtiyacınız varsa, işlevin nesne modeli boyunca nasıl dağıtılacağını ve denetim ile tüm alt nesneler arasındaki işlevselliği nasıl bölmeyeceğini saptayın. Bir nesne modeli, karmaşık bir denetim planlıyor veya çeşitli işlevler eklemek istiyorsanız yararlı olabilir.

3. İhtiyacınız olan denetimin türünü (örneğin, Kullanıcı denetimi, özel denetim, devralınan Windows Forms denetimi) saptayın. Ayrıntılar için bkz. [Denetim türü önerileri](control-type-recommendations.md) ve [Özel denetimlerin varielikler](varieties-of-custom-controls.md).

4. İşlevselliği, denetimin ve alt nesnelerin ya da yan yapılarının özellikleri, yöntemleri ve olayları olarak Express ve uygun erişim düzeyleri (örneğin, genel, korumalı vb.) atayın.

5. Denetiminiz için özel boyama gerekiyorsa, bunun için kod ekleyin. Ayrıntılar için bkz. [özel denetim boyama ve işleme](custom-control-painting-and-rendering.md).

6. Denetiminiz öğesinden <xref:System.Windows.Forms.UserControl>devralırsa, çalışma zamanı davranışını denetim projesini oluşturup **UserControl Test kapsayıcısında**çalıştırarak test edebilirsiniz. Daha fazla bilgi için [nasıl yapılır: UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)'un çalışma zamanı davranışını test edin.

7. Ayrıca, Windows uygulaması gibi yeni bir proje oluşturarak ve bir kapsayıcıya yerleştirerek denetiminizi test edebilir ve hatalarını ayıklayabilirsiniz. Bu işlem, izlenecek yolun bir [parçası olarak gösterilmiştir: Bileşik denetim](walkthrough-authoring-a-composite-control-with-visual-csharp.md)yazma.

8. Her bir özelliği eklerken, yeni işlevselliği uygulamak için test projenize özellikler ekleyin.

9. , Tasarımı iyileştirerek tekrarlayın.

10. Denetiminizi paketleyin ve dağıtın. Ayrıntılar için bkz. [Visual Studio 'da dağıtıma ilk bakış](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: UserControl sınıfından devralma](how-to-inherit-from-the-usercontrol-class.md)
- [Nasıl yapılır: Denetim sınıfından devralma](how-to-inherit-from-the-control-class.md)
- [Nasıl yapılır: Mevcut Windows Forms denetimlerinden devralma](how-to-inherit-from-existing-windows-forms-controls.md)
- [Nasıl yapılır: UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
