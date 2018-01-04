---
title: "Düzenlemelere ve Eylemsizliğe Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd31b89b-eab6-45a1-8d0b-11e0eb84b234
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6a0b8b62b997ab0dc7ff21375e82bda7e05d3c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="manipulations-and-inertia-overview"></a>Düzenlemelere ve Eylemsizliğe Genel Bakış
*İşlemeleri* taşıma, döndürme ve kullanarak kullanıcı arabirimi (UI) öğeleri yeniden boyutlandırın vermesine olanak sağlayan *manipülatörleri*. Bir manipulator fare temsil eder (bir senaryoda Dokunmatik özellikli) veya kalem veya bir parmak.  
  
 *Eylemsizlik* hızda uyuşmazlık zorlar öğelerde taklit ederek kullanıcı Arabirimi öğeleri için gerçek davranışını taklit eden. Bu, bir Dur gelen önce kendi taşıma (doğrusal ve Açısal) yavaş yavaş yavaş öğeleri sağlar. Bu makalede düzenlemeler ve eylemsizlik için .NET Framework tanıtılmaktadır.  
  
## <a name="manipulations"></a>İşlemeleri  
 Bir işleme manipülatörleri koleksiyonu bileşik bir nesne olarak değerlendirir. Bir uygulama, tek bileşenlerin yerine bileşik nesnesine değişiklikleri izleyebilirsiniz.  
  
 Aşağıdaki çizimde görüntüde göz önünde bulundurun. Bir kullanıcı iki manipülatörleri taşıma, döndürme ve görüntüyü ölçeklemek için kullanabilirsiniz. Her manipulator değişiklikleri birlikte diğer manipülatörleri yorumlanır.  
  
 Örneğin, iki manipülatörleri (1 ve 2) görüntüde varsa ve manipulator 1 içinde taşımak bir + Y yönünde (aşağı) görüntüye değişiklik bağlıdır ne manipulator 2 olur. Manipulator 2 ayrıca taşınırsa + Y yönünde (aşağı) görüntüsü yeterlidir taşır + Y yönünde. Ancak manipulator 2 değişmeyen veya (yukarı) -Y yönde giderse, görüntünün küçük veya Döndürülmüş yapılır.  
  
 ![İki parmakları düzenleme sanal bir fotoğraf. ] (../../../docs/framework/common-client-technologies/media/manipulation-resize.png "Manipulation_Resize")  
  
 İki manipülatörleri tarafından değiştirildiği bir görüntü  
  
 Denetleme işleme manipülatörleri kümesini izler ve bunlar birlikte çalışan bağımsız olarak yerine gibi bunları yorumlar bir çerçeve sağlar. İşlemci nesneleri aynı anda birden fazla işleme oluşturabilirsiniz bir uygulamada yönetilebilmesini her kullanıcı Arabirimi öğesi için bir tane. Bir işleme işlemci hangi izlemek için giriş aygıtları bildirilir ve aracılığıyla işlemeleri raporlar [.NET olayları](http://msdn.microsoft.com/library/17sde2xt.aspx).  
  
 Bir işleme işlemci değiştirildiği belirli öğeyle ilgili bilgi yok. Bir uygulama, ayrı ayrı bir uygulamaya özgü öğeye değişiklikleri uygular. Örneğin, bir uygulama görüntüye dönüşümleri uygular veya yeni konumunda ya yeni boyutu ya da yönlendirme görüntülemek için onu yeniden çizer.  
  
 İşlemeleri iki boyutlu (2-D için) tasarlanan [afin dönüşümler](http://msdn.microsoft.com/library/ms533810\(VS.85\).aspx). Bu dönüşümleri dahil Çevir, döndürün ve ölçeklendirin.  
  
### <a name="parts-of-a-manipulation"></a>Hareketin bölümleri  
 Bir işleme koleksiyonudur <xref:System.Windows.Input.Manipulations.Manipulator2D> nesneleri. Bu birleşik işleme elips ve bir başlangıç noktası ile temsil edilir. Başlangıç noktasını öğenin düzenleme tüm manipülatörleri ortalama konumudur. Elips kaynaktan ortalama uzaklık her biri için bir RADIUS sahip <xref:System.Windows.Input.Manipulations.Manipulator2D> nesneleri.  
  
 ![Hareketin bölümleri. ] (../../../docs/framework/common-client-technologies/media/manipulation-definition.png "Manipulation_Definition")  
  
 İki manipülatörleri (1 ve 2), bir kaynak ve elips düzenleme belirtin.  
  
 Manipülatörleri eklendiğinde, taşınabilir veya için bir kullanıcı Arabirimi öğesi kaldırıldığında gibi bir uygulama güncelleştirmeleri <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> çağırarak nesne <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> yöntemi. İşleme ilk başladığında <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> olayı oluşturulur.  
  
> [!NOTE]
>  Denetleme işleme tabanlı çerçeve güncelleştirme ortamda kullanıldığında daha verimli olur. XNA Framework'ü kullanarak tabanlı çerçeve güncelleştirmeler sağlayan bir Microsoft XNA uygulamasında işleme işleme kullanırken, bu ilgili bir sorun olmadığından [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) yöntemi. (Örneğin, WinForms) başka bir ortamda işlemeleri toplamak ve bunları düzenli aralıklarla göndermek için kendi tabanlı çerçeve mantığı sağlamanız gerekebilir <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> toplu olarak yöntemi.  
  
 Manipülatörleri veya kendi konumu değiştirme sayısı arttıkça <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> olayı oluşturulur. Özelliklerini <xref:System.Windows.Input.Manipulations.Manipulation2DDeltaEventArgs> geçirilir nesne <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> olay işleyicisi kaynak, Ölçek, döndürme ve son olay bu yana gerçekleşen çeviri değişiklikleri belirtin. İşleme kökeni manipülatörleri taşıdığınızda ve manipülatörleri eklendiğinde veya kaldırılan değiştirir. Çeviri değerlerini düzenleme içerir ne kadar X veya Y taşıma belirtin.  
  
 Yeni değerleri kullanarak, bir uygulama kullanıcı Arabirimi öğesi yeniden çizer.  
  
 ![Bir işleme contact A sonra sağa taşındı. ] (../../../docs/framework/common-client-technologies/media/manipulation-changed.png "Manipulation_Changed")  
  
 Manipulator 1 taşır ve değiştirmek kaynak neden olur.  
  
 Gelen düzenlenmesini ilişkili son manipulator kaldırıldığında <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> nesnesi <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> olayı oluşturulur.  
  
### <a name="the-manipulation-processing-model"></a>İşleme işlem modeli  
 Bir işleme işlemci doğrudan kullanım modeli kullanır. Bu basit model ile bir uygulama işleme işlemciyi tüm giriş olay ayrıntıları geçmesi gerekir. Bir giriş olayı, fare aygıtı, kalem veya bir parmak gibi basit herhangi bir giriş tarafından gerçekleştirilen. Bu işlem, doğrudan bir filtreleme mekanizması sunar ve gerekli olduğunda olayları uygulama toplu şekilde basit kullanım modeli, girdi.  
  
 Bir giriş ilkel işleme işleminde dahil etmek bir uygulama için oluşturduğu bir <xref:System.Windows.Input.Manipulations.Manipulator2D> giriş temel ayrıntılarını yapısından ve işleme kullanarak işlemci yapısı geçirir <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> yöntemi. İşleme işlemci ardından visual bileşen uygun bir şekilde güncelleştirmek için uygulama işlemelidir olayları başlatır.  
  
 ![Doğrudan işlemeleri akışını &#45; kullanım modeli. ] (../../../docs/framework/common-client-technologies/media/manipulation-flow.png "Manipulation_Flow")  
  
 İşleme işlem modeli  
  
## <a name="inertia"></a>Eylemsizlik  
 Eylemsizlik işlemci uygulamaları konumu, Yönlendirme ve diğer özellikleri UI öğesinin gerçek davranışını taklit ederek tahmin etmeniz için etkinleştirir.  
  
 Örneğin, bir kullanıcı bir öğeyi hareketleri, taşımaya devam, hızını düşürün ve yavaş durdurun. Eylemsizlik işlemci afin 2-D (kaynak, Ölçek, çeviri ve değerlerini döndürme) belirtilen yavaşlama oranı belirli bir zamanda üzerinden değiştirmek için neden olarak bu davranışı uygular.  
  
 Olarak işleme işlemeyle eylemsizlik işlemci herhangi belirli kullanıcı Arabirimi öğesi hakkında bilgi yok. Üzerinde ortaya olaylarına yanıt olarak bir <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> nesnesi, bir uygulama bir uygulamaya özgü öğesi için ayrı ayrı değişiklikleri uygular.  
  
 Eylemsizlik işleme ve denetleme işleme genellikle birlikte kullanılır. Arabirimlerini benzerdir ve bunlar Yükselt olaylar (bazı durumlarda) aynı. Genellikle, kullanıcı Arabirimi öğesi işlenmesini tamamlandığında eylemsizlik işleme başlar. Bu dinleme tarafından gerçekleştirilir <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> olay ve bu olay işleyiciden işleme eylemsizlik başlatılıyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Input.Manipulations>
