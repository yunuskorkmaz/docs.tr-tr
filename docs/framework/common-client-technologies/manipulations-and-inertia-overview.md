---
title: Düzenlemelere ve Eylemsizliğe Genel Bakış
ms.date: 03/30/2017
ms.assetid: dd31b89b-eab6-45a1-8d0b-11e0eb84b234
ms.openlocfilehash: 6396c174b341b5ae937fa931488ee1bd3a5fcbd5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187825"
---
# <a name="manipulations-and-inertia-overview"></a>Düzenlemelere ve Eylemsizliğe Genel Bakış
*İşlemeleri* taşımak, döndürmek ve kullanarak kullanıcı arabirimi (UI) öğeleri yeniden boyutlandırma kullanıcılara etkinleştirme *manipülatörleri*. Fare bir işleyiciyi temsil eder (bir senaryoda Dokunmatik özellikli) veya bir ekran kalemi veya bir parmağınızı.  
  
 *Eylemsizlik* hızda uyuşmazlıkları zorlar öğelerde benzetimini yaparak kullanıcı Arabirimi öğeleri için gerçek davranış öykünür. Bu öğeleri Durma noktasına gelen önce bunların taşıma (doğrusal ve angular) yavaş yavaş yavaş sağlar. Bu makalede, .NET Framework için düzenlemeleri ve Eylemsizliği giriş sağlar.  
  
## <a name="manipulations"></a>İşlemeleri  
 Bir işleme manipülatörleri koleksiyonunu bileşik bir nesnesi olarak değerlendirir. Bir uygulama, tek tek bileşenlerin yerine bileşik nesne değişikliklerini izleyebilirsiniz.  
  
 Aşağıdaki çizimde gösterilen görüntüyü göz önünde bulundurun. Bir kullanıcı, taşıma, döndürme ve görüntüyü ölçeklemek için iki manipülatörleri kullanabilirsiniz. Her işleyici yapılan değişiklikler ile birlikte diğer manipülatörleri yorumlanır.  
  
 Örneğin, görüntüde (1 ve 2) iki manipülatörleri varsa ve işleyici 1 içinde taşımak bir + Y yönünde (basılı), değişiklik görüntüye bağlıdır 2 işleyici için ne. Ayrıca geçtiğinde işleyici 2 + Y (basılı), görüntünün yalnızca hareket yönü + Y yönünde. Ancak işleyiciyi 2 değişmez ya da (up) -Y yönde hareket, görüntüyü daha küçük veya Döndürülmüş yapılır.  
  
 ![İki parmağın hareket ettiği sanal bir fotoğraf. ](../../../docs/framework/common-client-technologies/media/manipulation-resize.png "Manipulation_Resize")  
  
 İki manipülatörleri tarafından değiştirildiği bir görüntü  
  
 Düzenleme işlemi, bir alt kümesini manipülatörleri izleyen ve bunlar birlikte, hareket yerine bağımsız olarak varsa bunları yorumlar bir çerçeve sunar. İşlemci nesneleri aynı anda birden çok işleme oluşturabilirsiniz uygulamada yönetilebilmesini her kullanıcı Arabirimi öğesi için bir tane. Hangi cihazların gözlemleyin giriş bilgiye dayalı işleme işleyicisidir ve işlemeleri aracılığıyla raporları [.NET olayları](../../../docs/standard/events/index.md).  
  
 Bir işleme işlemci değiştirildiği belirli bir öğe hakkında bilgi yok. Bir uygulama, uygulamaya özgü öğeye değişiklikleri ayrı olarak uygular. Örneğin, bir uygulama görüntüye dönüşümleri uygular veya yeni konumunda ya da yeni bir boyut veya yönlendirme görüntülemek için yeniden çizer.  
  
 İşlemeleri, iki boyutlu (2B için) tasarlanmıştır [afin dönüşümler](/windows/desktop/gdiplus/-gdiplus-transformations-use). Bu dönüştürmeler dahil Çevir, döndürme ve ölçeklendirme.  
  
### <a name="parts-of-a-manipulation"></a>Bir işleme bölümleri  
 Bir işleme oluşan bir koleksiyondur <xref:System.Windows.Input.Manipulations.Manipulator2D> nesneleri. Bu toplu işleme, başlangıç noktası ve bir elips tarafından temsil edilir. Başlangıç noktasını bir öğeyi düzenleme tüm manipülatörleri ortalama konumudur. Her bir kaynaktan ortalama uzaklık bir RADIUS üç nokta işaretine sahip <xref:System.Windows.Input.Manipulations.Manipulator2D> nesneleri.  
  
 ![Bir işleme bölümleri. ](../../../docs/framework/common-client-technologies/media/manipulation-definition.png "Manipulation_Definition")  
  
 İki manipülatörleri (1 ve 2), bir kaynağı ve elips düzenleme belirtin  
  
 Manipülatörleri eklenen, taşınır veya kaldırılması için kullanıcı Arabirimi öğesi gibi bir uygulama güncelleştirmeleri <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> çağırarak <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> yöntemi. İşleme ilk başladığında <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> olayı oluşturulur.  
  
> [!NOTE]
> Düzenleme işlemi, bir çerçeve tabanlı güncelleştirme ortamında kullanıldığında daha verimli olur. XNA Framework'ü kullanarak çerçeve tabanlı güncelleştirmeleri sağladığından Microsoft XNA uygulamasında işlem işleme kullanırken, bu önemli değildir [Game.Update](https://docs.microsoft.com/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) yöntemi. (Örneğin, WinForms) başka bir ortamda işlemeleri toplamak ve bunları düzenli aralıklarla göndermek için kendi çerçeve tabanlı mantıksal sağlamanız gerekebilir <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> toplu olarak yöntemi.  
  
 Manipülatörleri veya konum değiştirme sayısı arttıkça <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> olayı oluşturulur. Özelliklerini <xref:System.Windows.Input.Manipulations.Manipulation2DDeltaEventArgs> geçirilen nesne <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> olay işleyicisi, kaynak, Ölçek, döndürme ve son olayın itibaren gerçekleşen çeviri değişiklikleri belirtin. İşleme kaynağı manipülatörleri taşıdığınızda ve manipülatörleri eklendiğinde veya kaldırıldığında değiştirir. Çeviri değerlerini düzenlemeyi içerir ne kadar X veya Y taşıma belirtin.  
  
 Yeni değerleri kullanarak, bir uygulama kullanıcı Arabirimi öğesi yeniden çizer.  
  
 ![Bir sözleşmeden bir işleme sağa taşındı. ](../../../docs/framework/common-client-technologies/media/manipulation-changed.png "Manipulation_Changed")  
  
 İşleyici 1 taşır ve değiştirmek kaynak neden olur  
  
 Gelen işleme ile ilişkili olan son işleyici kaldırıldığında <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> nesnesi <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> olayı oluşturulur.  
  
### <a name="the-manipulation-processing-model"></a>İşleme işlem modeli  
 Bir işleme işlemci doğrudan kullanım modeli kullanır. Bu basit model ile bir uygulama için işleme işlemci tüm giriş olayı ayrıntıları geçmesi gerekir. Bir giriş olayı, bir fare aygıtı, ekran kalemi veya nabzını gibi ilkel herhangi bir giriş tarafından gerçekleştirilen. Bu işlem, doğrudan bir filtreleme mekanizması sunar ve böylece uygulamanın toplu olarak güncelleştirebilen basit kullanım modeli, gerekli olduğunda olayları giriş.  
  
 Bir giriş temel düzenleme işlemine eklemek bir uygulama için oluşturduğu bir <xref:System.Windows.Input.Manipulations.Manipulator2D> giriş temel ayrıntılarını yapısından ve işleme kullanarak işlemci yapısı geçirir <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> yöntemi. İşleme işlemci visual bileşen uygun bir şekilde güncelleştirmek için uygulama işlemelidir olayları, ardından başlatır.  
  
 ![İşlemeleri doğrudan akışını&#45;kullanım modeli. ](../../../docs/framework/common-client-technologies/media/manipulation-flow.png "Manipulation_Flow")  
  
 İşleme işlem modeli  
  
## <a name="inertia"></a>Eylemsizlik  
 Uygulamalar, konum, Yönlendirme ve diğer UI öğesi özelliklerini gerçek davranış gibi davranarak tahmin etmek Eylemsizliği işlemci sağlar.  
  
 Örneğin, bir kullanıcı bir öğeyi hareketleri, taşımaya devam, yavaşlatma ve yavaş durdurun. İçin Eylemsizliği işlemcisi afin 2B değerleri (kaynak, Ölçek, çeviri ve döndürme) belirtilen yavaşlama oranı belirli bir zamanda üzerinden değiştirmek için neden olarak bu davranışı uygular.  
  
 Olarak işleme işlemeyle Eylemsizliği işlemci herhangi belirli kullanıcı Arabirimi öğesi hakkında bilgi yok. Üzerinde gerçekleşen olaylara yanıt olarak bir <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> nesnesi, bir uygulama ayrı bir uygulamaya özgü öğeye değişiklikleri uygular.  
  
 Eylemsizlik işleme ve düzenleme işlemi genellikle birlikte kullanılır. Arabirimlerini benzer ve bunlar Yükselt (bazı durumlarda) olaylardır aynı. Genellikle, kullanıcı Arabirimi öğesi düzenlenmesini tamamlandığında Eylemsizliği işleme başlar. Bu dinleme tarafından gerçekleştirilir <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> olay ve bu olay işleyiciden işleme Eylemsizliği başlatılıyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Input.Manipulations>
