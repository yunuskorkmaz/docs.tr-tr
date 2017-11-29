---
title: "İzlenecek Yol: Genişletilebilir Uygulama Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6609f30844421f94965fbe05114db96ed8edbb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-an-extensible-application"></a>İzlenecek Yol: Genişletilebilir Uygulama Oluşturma
Bu kılavuz, basit hesaplayıcı işlevler gerçekleştirdiği bir eklenti için bir işlem hattı oluşturma açıklar. Gerçek dünya senaryoları gösterilmemiştir; Bunun yerine, bir ardışık düzen ve nasıl bir eklenti için hizmetleri bir konak sağlayabilir temel işlevselliğini gösterir.  
  
 Bu kılavuz aşağıdaki görevler açıklanmaktadır:  
  
-   Visual Studio çözümü oluşturma.  
  
-   Ardışık Düzen dizin yapısı oluşturma.  
  
-   Sözleşme ve görünümler oluşturuluyor.  
  
-   Ekle tarafı bağdaştırıcısı oluşturuluyor.  
  
-   Konak tarafındaki bağdaştırıcı oluşturuluyor.  
  
-   Ana bilgisayar oluşturuluyor.  
  
-   Eklentisi oluşturuluyor.  
  
-   Ardışık Düzen dağıtma.  
  
-   Ana bilgisayar uygulaması çalışıyor.  
  
 Bu ardışık seri hale getirilebilir türler yalnızca geçirir (<xref:System.Double> ve <xref:System.String>), konak ve eklenti arasında. Karmaşık veri türlerinin koleksiyonları geçirmek nasıl oluşturulduğunu gösteren örnek için bkz: [izlenecek yol: konaklar arasında geçirme koleksiyonları ve eklentiler](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5).  
  
 Bu ardışık düzen sözleşme dört aritmetik işlemler bir nesne modelini tanımlar: ekleme, çıkarma, çarpma ve bölme. Eklenti konağa sonucunu döndürür ve ana bilgisayar 2 + 2 gibi hesaplamakta bir eşitlik eklenti sağlar.  
  
 Sürüm 2 hesaplayıcı eklentisi fazla hesaplama olasılıkları sağlar ve sürüm oluşturma gösterir. Bölümünde açıklanan [izlenecek yol: ana bilgisayar değişikliklerinizi olarak geriye dönük uyumluluk etkinleştirme](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdakiler gerekir:  
  
-   [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="creating-a-visual-studio-solution"></a>Visual Studio çözümü oluşturma  
 Bir çözümde kullanmak [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ardışık düzen segmentlerinizi projeleri içerecek biçimde.  
  
#### <a name="to-create-the-pipeline-solution"></a>Ardışık Düzen çözüm oluşturmak için  
  
1.  İçinde [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], adlı yeni bir proje oluşturma `Calc1Contract`. İçin temel **sınıf kitaplığı** şablonu.  
  
2.  Çözüm adı `CalculatorV1`.  
  
## <a name="creating-the-pipeline-directory-structure"></a>Ardışık Düzen dizin yapısı oluşturma  
 Eklenti modeli belirtilen dizin yapısında yerleştirilecek ardışık düzen segment derlemeler gerektirir. Ardışık Düzen yapısı hakkında daha fazla bilgi için bkz: [ardışık düzen geliştirme gereksinimleri](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
#### <a name="to-create-the-pipeline-directory-structure"></a>Ardışık Düzen dizin yapısını oluşturmak için  
  
1.  Bir uygulama klasörü herhangi bir yerden bilgisayarınızda oluşturun.  
  
2.  Bu klasörde aşağıdaki yapısını oluşturun:  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     Uygulama klasörünüzde ardışık düzen klasör yapısı koymak gerekli değildir; Ayrıca, yalnızca kolaylık sağlamak için burada yapılır. Uygun adımda Kılavuzu ardışık düzen klasör yapısı farklı bir konumda ise kodunu değiştirmek açıklanmaktadır. Ardışık Düzen directory gereksinimleri hakkında bilgi bkz [ardışık düzen geliştirme gereksinimleri](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
    > [!NOTE]
    >  `CalcV2` Klasör, bu kılavuzda kullanılmaz; için tutucudur [izlenecek yol: ana bilgisayar değişikliklerinizi olarak geriye dönük uyumluluk etkinleştirme](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="creating-the-contract-and-views"></a>Sözleşme ve görünümler oluşturma  
 Bu ardışık düzen sözleşme kesimini tanımlar `ICalc1Contract` dört yöntemleri tanımlar arabirimi: `add`, `subtract`, `multiply`, ve `divide`.  
  
#### <a name="to-create-the-contract"></a>Sözleşme oluşturmak için  
  
1.  Adlı Visual Studio çözümüne `CalculatorV1`, açık `Calc1Contract` projesi.  
  
2.  İçinde **Çözüm Gezgini**, aşağıdaki derlemelerine başvurular ekleyin `Calc1Contract` proje:  
  
     System.AddIn.Contract.dll  
  
     System.AddIn.dll  
  
3.  İçinde **Çözüm Gezgini**, yeni eklenen varsayılan sınıfı hariç **sınıf kitaplığı** projeleri.  
  
4.  İçinde **Çözüm Gezgini**, projesine yeni öğe eklemek kullanarak **arabirimi** şablonu. İçinde **Yeni Öğe Ekle** iletişim kutusunda, adı arabirimi `ICalc1Contract`.  
  
5.  Arabirim dosyasında ad alanı başvurularını ekleyin <xref:System.AddIn.Contract> ve <xref:System.AddIn.Pipeline>.  
  
6.  Bu sözleşme segment tamamlamak için aşağıdaki kodu kullanın. Bu arabirim olmalıdır Not <xref:System.AddIn.Pipeline.AddInContractAttribute> özniteliği.  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  İsteğe bağlı olarak, Visual Studio çözümü oluşturun. Son yordam, ancak her bir yordam her proje olmasını sağlar sonra derleme düzeltmeden çözüm çalıştırılamaz.  
  
 Eklenti görünümü ve konak görünümünü çünkü eklenti genellikle aynı kodu özellikle ilk sürümüne sahip bir eklenti, aynı anda kolayca görünümler oluşturabilirsiniz. Yalnızca bir faktörüyle farklı: eklenti görünümü gerektirir <xref:System.AddIn.Pipeline.AddInBaseAttribute> eklenti konak görünümünü öznitelikleri gerekmese özniteliği.  
  
#### <a name="to-create-the-add-in-view"></a>Eklenti görünümü oluşturmak için  
  
1.  Adlı yeni bir proje eklemek `Calc1AddInView` için `CalculatorV1` çözümü. İçin temel **sınıf kitaplığı** şablonu.  
  
2.  İçinde **Çözüm Gezgini**, System.AddIn.dll için bir başvuru ekleyin `Calc1AddInView` projesi.  
  
3.  İçinde **Çözüm Gezgini**, yeni eklenen varsayılan sınıfı hariç **sınıf kitaplığı** projeleri ve projesine yeni öğe eklemek kullanarak **arabirimi** şablonu. İçinde **Yeni Öğe Ekle** iletişim kutusunda, adı arabirimi `ICalculator`.  
  
4.  Ad alanı referansı arabirimi dosyasına ekleyin <xref:System.AddIn.Pipeline>.  
  
5.  Bu eklenti görünümü tamamlamak için aşağıdaki kodu kullanın. Bu arabirim olmalıdır Not <xref:System.AddIn.Pipeline.AddInBaseAttribute> özniteliği.  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  İsteğe bağlı olarak, Visual Studio çözümü oluşturun.  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a>Eklenti konak görünümünü oluşturmak için  
  
1.  Adlı yeni bir proje eklemek `Calc1HVA` için `CalculatorV1` çözümü. İçin temel **sınıf kitaplığı** şablonu.  
  
2.  İçinde **Çözüm Gezgini**, yeni eklenen varsayılan sınıfı hariç **sınıf kitaplığı** projeleri ve projesine yeni öğe eklemek kullanarak **arabirimi** şablonu. İçinde **Yeni Öğe Ekle** iletişim kutusunda, adı arabirimi `ICalculator`.  
  
3.  Arabirim dosyasında eklenti konak görünümünü tamamlamak için aşağıdaki kodu kullanın.  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  İsteğe bağlı olarak, Visual Studio çözümü oluşturun.  
  
## <a name="creating-the-add-in-side-adapter"></a>Ekleme tarafı bağdaştırıcısı oluşturma  
 Bu ekleme tarafı bağdaştırıcı bir görünüm sözleşme bağdaştırıcısı oluşur. Bu ardışık düzen segmenti türleri eklenti görünümünden sözleşmesine dönüştürür.  
  
 Bu ardışık düzendeki eklenti ana bilgisayara bir hizmet sunar ve ana bilgisayara akışı eklentiden türünü. Eklenti ana bilgisayardan akışı hiçbir türünü olduğundan, bu ardışık düzen eklenti tarafı sözleşme görünümü bağdaştırıcısında eklemek zorunda değil.  
  
#### <a name="to-create-the-add-in-side-adapter"></a>Ekle tarafı bağdaştırıcısı oluşturmak için  
  
1.  Adlı yeni bir proje eklemek `Calc1AddInSideAdapter` için `CalculatorV1` çözümü. İçin temel **sınıf kitaplığı** şablonu.  
  
2.  İçinde **Çözüm Gezgini**, aşağıdaki derlemelerine başvurular ekleyin `Calc1AddInSideAdapter` proje:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Proje başvurularını bitişik ardışık düzen kesimlerin projelerine ekleyin:  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  Her proje başvurusu seçin ve **özellikleri** ayarlamak **kopya yerel** için **False**. Visual Basic'teki **başvuruları** sekmesinde **proje özelliklerini** ayarlamak için **kopya yerel** için **False** iki proje başvuruları için.  
  
5.  Projenin varsayılan sınıfı yeniden adlandırma `CalculatorViewToContractAddInSideAdapter`.  
  
6.  Sınıf dosyasında için ad alanı başvurularını ekleyin <xref:System.AddIn.Pipeline>.  
  
7.  Sınıf dosyasında bitişik parçaları için ad alanı başvurularını ekleyin: `CalcAddInViews` ve `CalculatorContracts`. (Visual Basic'te, bu ad alanı başvurularını olan `Calc1AddInView.CalcAddInViews` ve `Calc1Contract.CalculatorContracts`, Visual Basic projeleri varsayılan ad alanlarını devre dışı bırakmış sürece.)  
  
8.  Uygulama <xref:System.AddIn.Pipeline.AddInAdapterAttribute> özniteliğini `CalculatorViewToContractAddInSideAdapter` Ekle tarafı bağdaştırıcı olarak belirlemek için sınıf.  
  
9. Olun `CalculatorViewToContractAddInSideAdapter` sınıfı <xref:System.AddIn.Pipeline.ContractBase>, bir varsayılan uygulaması sağlayan <xref:System.AddIn.Contract.IContract> arabirim ve ardışık düzeni için sözleşme arabirimini uygulayan `ICalc1Contract`.  
  
10. Kabul ortak bir oluşturucu ekleyin bir `ICalculator`, özel bir alana önbelleğe alır ve temel sınıf oluşturucu çağırır.  
  
11. Üyeleri uygulamak için `ICalc1Contract`, yalnızca ilgili üyeleri çağrı `ICalculator` örneğinin oluşturucuya geçirilen ve sonuçları döndürür. Bu görünüm uyum (`ICalculator`) sözleşmeye (`ICalc1Contract`).  
  
     Aşağıdaki kod tamamlanmış eklemek tarafı bağdaştırıcı gösterir.  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. İsteğe bağlı olarak, Visual Studio çözümü oluşturun.  
  
## <a name="creating-the-host-side-adapter"></a>Konak tarafındaki bağdaştırıcısı oluşturma  
 Bu ana bilgisayar tarafı bağdaştırıcı bir sözleşme görünümü bağdaştırıcısı oluşur. Bu kesimin eklenti konak görünümünü sözleşmesine uyum sağlar.  
  
 Bu ardışık düzeninde eklenti bir hizmet ana bilgisayarı ve türleri akış bileşeninden Ekle ana bilgisayara sağlar. Eklenti ana bilgisayardan akışı hiçbir türünü olduğundan, bir görünüm sözleşme bağdaştırıcısı içeriyor gerekmez.  
  
 Ömür Yönetimi uygulamak için kullandığınız bir <xref:System.AddIn.Pipeline.ContractHandle> sözleşmesine ömrü belirteci eklemek için nesne. Çalışmak yaşam süresi Management sırayla bu işlemek için bir başvuru tutmanız gerekir. Belirteç uygulandıktan sonra ek bir programlamaya artık kullanılıyor ve atık toplama için kullanılabilmesini eklenti sistemi nesnelerin dispose çünkü gereklidir. Daha fazla bilgi için bkz: [yaşam süresi Management](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
#### <a name="to-create-the-host-side-adapter"></a>Konak tarafındaki bağdaştırıcısı oluşturmak için  
  
1.  Adlı yeni bir proje eklemek `Calc1HostSideAdapter` için `CalculatorV1` çözümü. İçin temel **sınıf kitaplığı** şablonu.  
  
2.  İçinde **Çözüm Gezgini**, aşağıdaki derlemelerine başvurular ekleyin `Calc1HostSideAdapter` proje:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Proje başvurularını bitişik parçaları projelerine ekleyin:  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  Her proje başvurusu seçin ve **özellikleri** ayarlamak **kopya yerel** için **False**. Visual Basic'teki **başvuruları** sekmesinde **proje özelliklerini** ayarlamak için **kopya yerel** için **False** iki proje başvuruları için.  
  
5.  Projenin varsayılan sınıfı yeniden adlandırma `CalculatorContractToViewHostSideAdapter`.  
  
6.  Sınıf dosyasında için ad alanı başvurularını ekleyin <xref:System.AddIn.Pipeline>.  
  
7.  Sınıf dosyasında bitişik parçaları için ad alanı başvurularını ekleyin: `CalcHVAs` ve `CalculatorContracts`. (Visual Basic'te, bu ad alanı başvurularını olan `Calc1HVA.CalcHVAs` ve `Calc1Contract.CalculatorContracts`, Visual Basic projeleri varsayılan ad alanlarını devre dışı bırakmış sürece.)  
  
8.  Uygulama <xref:System.AddIn.Pipeline.HostAdapterAttribute> özniteliğini `CalculatorContractToViewHostSideAdapter` konak tarafı bağdaştırıcısı kesim olarak belirlemek için sınıf.  
  
9. Olun `CalculatorContractToViewHostSideAdapter` sınıf eklenti konak görünümünü temsil eden arabirim uygulama: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` Visual Basic'te).  
  
10. Ardışık Düzen sözleşme türü kabul eden bir ortak oluşturucu ekleyin `ICalc1Contract`. Oluşturucusu sözleşme referansı önbelleğe gerekir. Bu ayrıca oluşturabilir ve yeni bir önbellek <xref:System.AddIn.Pipeline.ContractHandle> ömrünü yönetmek için sözleşmesi için.  
  
    > [!IMPORTANT]
    >  <xref:System.AddIn.Pipeline.ContractHandle> Ömür yönetimi için kritik öneme sahiptir. Bir başvuru tutmak başarısız olursa <xref:System.AddIn.Pipeline.ContractHandle> nesne, atık toplama, geri ve ardışık düzen programınızı beklemiyor zaman kapanacak. Bu tanılama, gibi zor olan hatalara yol açabilir <xref:System.AppDomainUnloadedException>. Bu yüzden bu durum bir hata olduğunu tespit etmek üzere yaşam süresi management kod yolu kapatma bir ardışık düzen yaşamında normal bir aşamadır.  
  
11. Üyeleri uygulamak için `ICalculator`, yalnızca ilgili üyeleri çağrı `ICalc1Contract` örneğinin oluşturucuya geçirilen ve sonuçları döndürür. Bu sözleşme uyum (`ICalc1Contract`) görüntülemek için (`ICalculator`).  
  
     Aşağıdaki kod tamamlanmış konak tarafı bağdaştırıcısı gösterir.  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. İsteğe bağlı olarak, Visual Studio çözümü oluşturun.  
  
## <a name="creating-the-host"></a>Konak oluşturma  
 Bir ana bilgisayar uygulaması eklentisi eklenti konak görünümünü üzerinden ile etkileşim kurar. Tarafından sağlanan eklenti bulma ve etkinleştirme yöntemlerini kullanan <xref:System.AddIn.Hosting.AddInStore> ve <xref:System.AddIn.Hosting.AddInToken> sınıfları aşağıdakileri yapın:  
  
-   Ardışık Düzen ve eklenti bilgilerini önbelleğini güncelleştirin.  
  
-   Eklentiler ana görünüm türü bulmak `ICalculator`, belirtilen ardışık düzen kök dizininin altında.  
  
-   Hangi kullanmak için eklenti belirtmek için kullanıcıya sor.  
  
-   Seçili eklenti belirtilen güvenlik güven düzeyine sahip yeni bir uygulama etki alanında etkinleştirin.  
  
-   Özel çalıştırmak `RunCalculator` eklentinin eklenti konak görünümünü tarafından belirtilen yöntemlerini çağıran yöntemi.  
  
#### <a name="to-create-the-host"></a>Ana bilgisayar oluşturmak için  
  
1.  Adlı yeni bir proje eklemek `Calc1Host` için `CalculatorV1` çözümü. İçin temel **konsol uygulaması** şablonu.  
  
2.  İçinde **Çözüm Gezgini**, System.AddIn.dll derlemesine başvuru ekleyin `Calc1Host` projesi.  
  
3.  Proje için bir başvuru ekleyin `Calc1HVA` projesi. Proje başvurusu seçin ve **özellikleri** ayarlamak **kopya yerel** için **False**. Visual Basic'teki **başvuruları** sekmesinde **proje özelliklerini** ayarlamak için **kopya yerel** için **False**.  
  
4.  Sınıf dosyası (Visual Basic modülünde) yeniden adlandırma `MathHost1`.  
  
5.  Visual Basic'teki **uygulama** sekmesinde **proje özelliklerini** ayarlamak için iletişim kutusunu **Başlangıç nesnesi** için **Sub Main**.  
  
6.  Sınıf veya Modülü dosyasında ad alanı için bir başvuru ekleyin <xref:System.AddIn.Hosting>.  
  
7.  Sınıf veya Modülü dosyasında eklenti konak görünümünü ad alanı başvurusunu ekleyin: `CalcHVAs`. (Visual Basic'te, bu ad alanı başvurudur `Calc1HVA.CalcHVAs`, Visual Basic projeleri varsayılan ad alanlarını devre dışı bırakmış sürece.)  
  
8.  İçinde **Çözüm Gezgini**, çözümü seçin ve **proje** menüsünü seçin **özellikleri**. İçinde **çözüm özellik sayfaları** iletişim kutusu, kümesi **tek başlangıç projesi** bu ana bilgisayar uygulaması projesi olmalıdır.  
  
9. Sınıf veya Modülü dosyasında kullanmak <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> önbelleğini güncelleştirmeye yöntemi. Kullanmak <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> belirteçleri koleksiyonunu alma ve kullanmak için yöntem <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> bir eklentiyi etkinleştirmek için yöntemi.  
  
     Aşağıdaki kod tamamlanmış ana bilgisayar uygulamasını gösterir.  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  Bu kod, ardışık düzen klasör yapısı uygulama klasöründe bulunduğunu varsayar. Başka bir yerde bulunan ayarlar kod satırı tıklarsanız `addInRoot` değişken, böylece değişkeni ardışık düzen directory yapınızı yolunu içerir.  
  
     Kod kullanan bir `ChooseCalculator` yöntemi belirteçleri listelemek için ve kullanıcıdan bir eklenti seçin. `RunCalculator` Yöntemi basit aritmetik ifadeler için kullanıcıdan, kullanarak ifadeler ayrıştırır `Parser` sınıfı ve sonuçları döndürdü eklenti tarafından görüntüler.  
  
10. İsteğe bağlı olarak, Visual Studio çözümü oluşturun.  
  
## <a name="creating-the-add-in"></a>Eklentiyi oluşturma  
 Bir eklenti eklenti görünümü tarafından belirtilen yöntemlerini uygular. Bu eklenti uygulayan `Add`, `Subtract`, `Multiply`, ve `Divide` işlemler ve ana bilgisayar için sonuçları döndürür.  
  
#### <a name="to-create-the-add-in"></a>Eklenti oluşturmak için  
  
1.  Adlı yeni bir proje eklemek `AddInCalcV1` için `CalculatorV1` çözümü. İçin temel **sınıf kitaplığı** şablonu.  
  
2.  İçinde **Çözüm Gezgini**, projeye System.AddIn.dll derlemesine başvuru ekleyin.  
  
3.  Proje için bir başvuru ekleyin `Calc1AddInView` projesi. Proje başvurusu seçin ve **özellikleri**ayarlayın **kopya yerel** için **False**. Visual Basic'teki **başvuruları** sekmesinde **proje özelliklerini** ayarlamak için **kopya yerel** için **False** proje başvurusu için.  
  
4.  Sınıfı yeniden adlandırma `AddInCalcV1`.  
  
5.  Sınıf dosyasında, ad alanı için bir başvuru ekleyin <xref:System.AddIn> ve eklenti görünümü kesimi: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` Visual Basic'te).  
  
6.  Uygulama <xref:System.AddIn.AddInAttribute> özniteliğini `AddInCalcV1` sınıfı bir eklenti olarak belirlemek için sınıf.  
  
7.  Olun `AddInCalcV1` sınıf eklenti görünümü temsil eden arabirim uygulama: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` Visual Basic'te).  
  
8.  Üyelerini uygulama `ICalculator` uygun hesaplamaların sonuçlarını döndürerek.  
  
     Tamamlanan eklentisi aşağıdaki kodu gösterir.  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. İsteğe bağlı olarak, Visual Studio çözümü oluşturun.  
  
## <a name="deploying-the-pipeline"></a>Ardışık Düzen dağıtma  
 Şimdi oluşturmak ve eklenti parçaları için gerekli ardışık düzen dizin yapısını dağıtmak hazır olursunuz.  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a>Ardışık düzene kesimleri dağıtmak için  
  
1.  Çözümdeki her proje için kullanmak **yapı** sekmesinde **proje özelliklerini** ( **derleme** sekmesini Visual Basic'te) değerini ayarlamak için **çıkış yolu**  ( **yapı çıkış yolu** Visual Basic'te). Uygulama klasörünüzde adlandırırsanız `MyApp`, örneğin, projelerinizi aşağıdaki klasörler halinde oluşturmayı tercih:  
  
    |Project|Yol|  
    |-------------|----------|  
    |AddInCalcV1|MyApp\Pipeline\AddIns\CalcV1|  
    |Calc1AddInSideAdapter|MyApp\Pipeline\AddInSideAdapters|  
    |Calc1AddInView|MyApp\Pipeline\AddInViews|  
    |Calc1Contract|MyApp\Pipeline\Contracts|  
    |Calc1Host|Uygulamam|  
    |Calc1HostSideAdapter|MyApp\Pipeline\HostSideAdapters|  
    |Calc1HVA|Uygulamam|  
  
    > [!NOTE]
    >  Uygulama klasörü dışında bir konumda ardışık düzen klasör yapısı almaya karar verdiyseniz, buna göre tabloda gösterilen yolları değiştirmeniz gerekir. Ardışık Düzen directory gereksinimleri hakkında bilgi bkz [ardışık düzen geliştirme gereksinimleri](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
2.  Visual Studio çözümü oluşturun.  
  
3.  Derlemeler için doğru dizinleri kopyalanan ve derlemeler hiçbir ek kopyalarını yanlış klasörlerde yüklenen emin olmak için uygulama ve ardışık düzen dizinleri denetleyin.  
  
    > [!NOTE]
    >  Değil değiştirirseniz **kopya yerel** için **False** için `Calc1AddInView` proje başvurusu'nda `AddInCalcV1` projesi, yükleyici bağlamı sorunları engeller eklenti bulunan gelen.  
  
     Ardışık düzene dağıtma hakkında daha fazla bilgi için bkz: [ardışık düzen geliştirme gereksinimleri](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
## <a name="running-the-host-application"></a>Ana bilgisayar uygulamasını çalıştırma  
 Şimdi konak çalıştırın ve eklentisi ile etkileşim kurmak hazırsınız.  
  
#### <a name="to-run-the-host-application"></a>Ana bilgisayar uygulamasını çalıştırmak için  
  
1.  Komut isteminde uygulama dizinine gidin ve ana bilgisayar uygulamasını çalıştırmak `Calc1Host.exe`.  
  
2.  Ana bilgisayar tüm kullanılabilir eklentiler türüne bulur ve bir eklenti seçmenizi ister. Girin **1** için yalnızca eklentisi.  
  
3.  Bir eşitlik için hesaplayıcı, gibi girin **2 + 2**. Alanları numaraları işleci arasında olması gerekir.  
  
4.  Tür **çıkmak** ve basın **Enter** uygulamayı kapatmak için anahtar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Ana bilgisayar değişikliklerinizi olarak geriye dönük uyumluluk etkinleştirme](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [İzlenecek yol: Geçirme koleksiyonları arasında konakları ve eklentiler](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [Ardışık Düzen geliştirme gereksinimleri](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [Sözleşmeler, görünümler ve bağdaştırıcıları](http://msdn.microsoft.com/en-us/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [Ardışık Düzen geliştirme](../../../docs/framework/add-ins/pipeline-development.md)
