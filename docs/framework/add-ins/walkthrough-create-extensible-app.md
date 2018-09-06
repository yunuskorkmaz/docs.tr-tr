---
title: 'İzlenecek Yol: Genişletilebilir Uygulama Oluşturma'
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d2aaeaffaf3abbe1e8efcdb57d40e6ae60f89b5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875102"
---
# <a name="walkthrough-creating-an-extensible-application"></a>İzlenecek Yol: Genişletilebilir Uygulama Oluşturma
Bu izlenecek yol basit hesap makinesi işlevlerini gerçekleştiren bir eklenti için bir işlem hattı oluşturmayı açıklar. Gerçek dünya senaryoları göstermemiz gerekmez; Bunun yerine, bir işlem hattı ve nasıl bir eklenti için bir ana bilgisayar hizmetleri sağlayabilir temel işlevlerini gösterir.  
  
 Bu izlenecek yol aşağıdaki görevleri açıklanmaktadır:  
  
-   Visual Studio çözümü oluşturuluyor.  
  
-   İşlem hattı dizin yapısı oluşturma.  
  
-   Sözleşme ve görünümler oluşturuluyor.  
  
-   Ekle tarafı bağdaştırıcısı oluşturuluyor.  
  
-   Konak tarafı bağdaştırıcısı oluşturuluyor.  
  
-   Ana bilgisayarı oluşturma.  
  
-   Eklenti oluşturma.  
  
-   İşlem hattı dağıtılıyor.  
  
-   Ana bilgisayar uygulaması çalışıyor.  
  
 Bu işlem hattı yalnızca serializable türler geçirir (<xref:System.Double> ve <xref:System.String>), konak ile eklenti arasındaki. Karmaşık veri türlerini koleksiyonlarının nasıl gösteren bir örnek için bkz: [izlenecek yol: koleksiyonları konaklar arasında geçirme ve eklentileri](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).  
  
 Bu işlem hattı için anlaşma dört aritmetik işlemler bir nesne modelini tanımlar: ekleme, çıkarma, çarpma ve bölme. Ana bilgisayar 2 + 2 gibi hesaplanacak Denklem eklenti sağlar ve eklenti konağa sonuç döndürür.  
  
 Sürüm 2 hesaplayıcı eklentisinin daha hesaplama olanaklar sağlar ve sürüm oluşturmayı gösterir. İçinde açıklanan [izlenecek yol: ana bilgisayar değişikliklerinizi olarak geriye dönük uyumluluk etkinleştirme](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdakiler gerekir:  
  
-   Visual Studio.  
  
## <a name="creating-a-visual-studio-solution"></a>Visual Studio çözümü oluşturma  
 Bir çözümü Visual Studio'da projeler, ardışık düzeni segmentlerini içerecek şekilde kullanın.  
  
#### <a name="to-create-the-pipeline-solution"></a>İşlem hattı oluşturmak için  
  
1.  Visual Studio'da adlı yeni bir proje oluşturun `Calc1Contract`. Bu temel **sınıf kitaplığı** şablonu.  
  
2.  Çözüm adı `CalculatorV1`.  
  
## <a name="creating-the-pipeline-directory-structure"></a>İşlem hattı dizin yapısı oluşturma  
 Eklenti modeli, işlem hattı segment derlemeleri belirtilen dizin yapısında yerleştirilmesini gerektirir. İşlem hattı yapısı hakkında daha fazla bilgi için bkz. [ardışık düzen geliştirme gereksinimleri](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
#### <a name="to-create-the-pipeline-directory-structure"></a>İşlem hattı dizin yapısı oluşturmak için  
  
1.  Bir uygulama klasörü herhangi bir yere bilgisayarınızda oluşturun.  
  
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
  
     İşlem hattı klasör yapısını uygulama klasörünüzde koymak gerekli değildir; Ayrıca, yalnızca kolaylık sağlamak için burada yapılır. Uygun adımda, işlem hattı klasör yapısının farklı bir konumda ise, kod değiştirme gözden geçirme açıklanmaktadır. İşlem hattı dizin gereksinimleri bkz [ardışık düzen geliştirme gereksinimleri](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
    > [!NOTE]
    >  `CalcV2` Klasör, bu izlenecek yolda kullanılamıyor; bunun için bir yer tutucu [izlenecek yol: ana bilgisayar değişikliklerinizi olarak geriye dönük uyumluluk etkinleştirme](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="creating-the-contract-and-views"></a>Sözleşme ve görünümler oluşturma  
 Bu işlem hattı sözleşme kesimin tanımlar `ICalc1Contract` dört yöntemi tanımlayan arabirim: `add`, `subtract`, `multiply`, ve `divide`.  
  
#### <a name="to-create-the-contract"></a>Sözleşme oluşturmak için  
  
1.  Visual Studio çözümünde adlı `CalculatorV1`açın `Calc1Contract` proje.  
  
2.  İçinde **Çözüm Gezgini**, aşağıdaki derlemelere başvurular ekleyin `Calc1Contract` proje:  
  
     System.AddIn.Contract.dll  
  
     System.AddIn.dll  
  
3.  İçinde **Çözüm Gezgini**, yeni eklenen varsayılan sınıfı hariç **sınıf kitaplığı** projeleri.  
  
4.  İçinde **Çözüm Gezgini**, projeye yeni bir öğe eklemek kullanarak **arabirimi** şablonu. İçinde **Yeni Öğe Ekle** iletişim kutusunda adı arabirim `ICalc1Contract`.  
  
5.  Arabirimi dosyasında, ad alanı başvurularını ekleyin <xref:System.AddIn.Contract> ve <xref:System.AddIn.Pipeline>.  
  
6.  Bu sözleşme parçasını tamamlamak için aşağıdaki kodu kullanın. Bu arabirim olmalıdır Not <xref:System.AddIn.Pipeline.AddInContractAttribute> özniteliği.  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  İsteğe bağlı olarak, Visual Studio çözümü oluşturun. Çözüm, son yordamı, ancak her yordam, her proje olmasını sağlar, sonra onu oluşturmak düzeltene kadar çalıştırılamaz.  
  
 Eklenti görünümü ve ana görünümünde eklenti genellikle aynı kodu, özellikle ilk sürümüne sahip bir eklenti içinde aynı anda kolayca görünümler oluşturabilirsiniz. Bunların değişiklik gösterdiği bir faktör: eklenti görünümü gerektirir <xref:System.AddIn.Pipeline.AddInBaseAttribute> eklentisinin ana görünümünde herhangi bir özniteliği ihtiyacı olmasa da, öznitelik.  
  
#### <a name="to-create-the-add-in-view"></a>Eklenti görünümü oluşturmak için  
  
1.  Adlı yeni bir proje ekleyin `Calc1AddInView` için `CalculatorV1` çözüm. Bu temel **sınıf kitaplığı** şablonu.  
  
2.  İçinde **Çözüm Gezgini**, System.AddIn.dll için bir başvuru ekleyin `Calc1AddInView` proje.  
  
3.  İçinde **Çözüm Gezgini**, yeni eklenen varsayılan sınıfı hariç **sınıf kitaplığı** projeleri ve proje için yeni bir öğe eklemek kullanarak **arabirimi** şablonu. İçinde **Yeni Öğe Ekle** iletişim kutusunda adı arabirim `ICalculator`.  
  
4.  Ad alanı başvuru arabirimi dosyasına ekleyin <xref:System.AddIn.Pipeline>.  
  
5.  Bu eklenti görünümü tamamlamak için aşağıdaki kodu kullanın. Bu arabirim olmalıdır Not <xref:System.AddIn.Pipeline.AddInBaseAttribute> özniteliği.  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  İsteğe bağlı olarak, Visual Studio çözümü oluşturun.  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a>Eklentinin ana bilgisayar görünümü oluşturmak için  
  
1.  Adlı yeni bir proje ekleyin `Calc1HVA` için `CalculatorV1` çözüm. Bu temel **sınıf kitaplığı** şablonu.  
  
2.  İçinde **Çözüm Gezgini**, yeni eklenen varsayılan sınıfı hariç **sınıf kitaplığı** projeleri ve proje için yeni bir öğe eklemek kullanarak **arabirimi** şablonu. İçinde **Yeni Öğe Ekle** iletişim kutusunda adı arabirim `ICalculator`.  
  
3.  Arabirimi dosyasında, eklentinin ana görünümünde tamamlamak için aşağıdaki kodu kullanın.  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  İsteğe bağlı olarak, Visual Studio çözümü oluşturun.  
  
## <a name="creating-the-add-in-side-adapter"></a>Ekleme tarafı bağdaştırıcısı oluşturma  
 Bu ekleme tarafı bağdaştırıcısı bir görünüm ve sözleşme bağdaştırıcısı oluşur. Bu işlem Hattı Kesim türleri eklenti görünümünden Anlaşmadaki dönüştürür.  
  
 Bu işlem hattı eklenti konağa bir hizmet sağlar ve türleri eklentisi konağa akış. Eklentinin ana bilgisayardan tür akış olduğundan, bu işlem hattı eklenti tarafındaki bir sözleşme ve görünüm bağdaştırıcısı dahil gerekmez.  
  
#### <a name="to-create-the-add-in-side-adapter"></a>Ekle tarafı bağdaştırıcısı oluşturmak için  
  
1.  Adlı yeni bir proje ekleyin `Calc1AddInSideAdapter` için `CalculatorV1` çözüm. Bu temel **sınıf kitaplığı** şablonu.  
  
2.  İçinde **Çözüm Gezgini**, aşağıdaki derlemelere başvurular ekleyin `Calc1AddInSideAdapter` proje:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Bitişik ardışık düzeni segmentlerini projelerde proje başvuruları ekleyin:  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  Her bir proje başvurusu seçin ve **özellikleri** ayarlamak **Yereli Kopyala** için **False**. Visual Basic'teki **başvuruları** sekmesinde **proje özellikleri** ayarlanacak **Yereli Kopyala** için **False** iki proje başvuruları için.  
  
5.  Projenin varsayılan sınıfı Yeniden Adlandır `CalculatorViewToContractAddInSideAdapter`.  
  
6.  Sınıf dosyasında ad alanı başvurularını ekleyin <xref:System.AddIn.Pipeline>.  
  
7.  Sınıf dosyasında bitişik parçaları için ad alanı başvurularını ekleyin: `CalcAddInViews` ve `CalculatorContracts`. (Visual Basic'te bu ad alanı başvurularını olan `Calc1AddInView.CalcAddInViews` ve `Calc1Contract.CalculatorContracts`sürece, Visual Basic projelerinde varsayılan ad alanlarını devre dışı bırakmış.)  
  
8.  Uygulama <xref:System.AddIn.Pipeline.AddInAdapterAttribute> özniteliğini `CalculatorViewToContractAddInSideAdapter` sınıfı Ekle tarafı bağdaştırıcısı olarak tanımlamak için.  
  
9. Olun `CalculatorViewToContractAddInSideAdapter` sınıfı <xref:System.AddIn.Pipeline.ContractBase>, varsayılan bir uygulama sağlayan <xref:System.AddIn.Contract.IContract> arabirim ve işlem hattının anlaşma arabirimi uygulayan `ICalc1Contract`.  
  
10. Kabul eden bir Genel oluşturucu ekleyin bir `ICalculator`, özel bir alanda önbelleğe alır ve temel sınıf oluşturucusunu çağırır.  
  
11. Üyeleri uygulamak için `ICalc1Contract`, karşılık gelen üyelerini çağırarak yeterlidir `ICalculator` örneği oluşturucuya geçirilir ve sonuçlar döndürür. Bu görünüm uyum sağlayan (`ICalculator`) sözleşmeye (`ICalc1Contract`).  
  
     Aşağıdaki kod, tamamlanan ekleme tarafı bağdaştırıcısı gösterir.  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. İsteğe bağlı olarak, Visual Studio çözümü oluşturun.  
  
## <a name="creating-the-host-side-adapter"></a>Konak tarafı bağdaştırıcısı oluşturma  
 Bu konak tarafı bağdaştırıcı bir sözleşme ve görünüm bağdaştırıcısı oluşur. Bu kesimin eklentisinin ana görünümünde Anlaşmadaki uyum sağlar.  
  
 Bu işlem hattı, eklenti hizmet ana bilgisayarı ve türleri flow'a eklenti konağa sağlar. Eklentinin ana bilgisayardan tür akış olduğundan, bir görünüm ve sözleşme bağdaştırıcısı dahil gerekmez.  
  
 Ömür Yönetimi uygulamak için kullanmak bir <xref:System.AddIn.Pipeline.ContractHandle> Anlaşmadaki bir ömrü belirteci eklemek için nesne. Sırayla çalışması ömür yönetimi için bu tutamacı başvuru tutmanız gerekir. Artık kullanılmayan ve çöp toplama için kullanılabilir hale getirmek eklenti sistem nesneleri atmak çünkü belirteç uygulandıktan sonra ek programlama gereklidir. Daha fazla bilgi için [ömür Yönetimi](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
#### <a name="to-create-the-host-side-adapter"></a>Konak tarafı bağdaştırıcısı oluşturmak için  
  
1.  Adlı yeni bir proje ekleyin `Calc1HostSideAdapter` için `CalculatorV1` çözüm. Bu temel **sınıf kitaplığı** şablonu.  
  
2.  İçinde **Çözüm Gezgini**, aşağıdaki derlemelere başvurular ekleyin `Calc1HostSideAdapter` proje:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Bitişik parçaları için proje proje başvurular ekleyin:  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  Her bir proje başvurusu seçin ve **özellikleri** ayarlamak **Yereli Kopyala** için **False**. Visual Basic'teki **başvuruları** sekmesinde **proje özellikleri** ayarlanacak **Yereli Kopyala** için **False** iki proje başvuruları için.  
  
5.  Projenin varsayılan sınıfı Yeniden Adlandır `CalculatorContractToViewHostSideAdapter`.  
  
6.  Sınıf dosyasında ad alanı başvurularını ekleyin <xref:System.AddIn.Pipeline>.  
  
7.  Sınıf dosyasında bitişik parçaları için ad alanı başvurularını ekleyin: `CalcHVAs` ve `CalculatorContracts`. (Visual Basic'te bu ad alanı başvurularını olan `Calc1HVA.CalcHVAs` ve `Calc1Contract.CalculatorContracts`sürece, Visual Basic projelerinde varsayılan ad alanlarını devre dışı bırakmış.)  
  
8.  Uygulama <xref:System.AddIn.Pipeline.HostAdapterAttribute> özniteliğini `CalculatorContractToViewHostSideAdapter` konak tarafı bağdaştırıcısı kesim olarak tanımlamak için sınıfı.  
  
9. Olun `CalculatorContractToViewHostSideAdapter` sınıf uygulama ana görünümünde eklentisinin temsil eden arabirim: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` Visual Basic'te).  
  
10. İşlem hattı sözleşme türü kabul eden bir Genel oluşturucu ekleyin `ICalc1Contract`. Oluşturucu sözleşmesine başvuru önbellek gerekir. Bu ayrıca oluşturabilir ve yeni bir önbellek <xref:System.AddIn.Pipeline.ContractHandle> ömrünü yönetmek için sözleşmeyi için.  
  
    > [!IMPORTANT]
    >  <xref:System.AddIn.Pipeline.ContractHandle> Ömür yönetimi için kritik öneme sahiptir. Başvuru tutmak başarısız olursa <xref:System.AddIn.Pipeline.ContractHandle> nesne, çöp toplama, geri ve işlem hattı, programınızın beklemediğinden kapanır. Bu gibi tanılama zor olan hatalara yol <xref:System.AppDomainUnloadedException>. Bu durum bir hata olduğunu tespit etmek ömrü Yönetimi kod bir yolu olmasını kapatma bir işlem hattı, yaşamında normal bir aşamayı ifade eder.  
  
11. Üyeleri uygulamak için `ICalculator`, karşılık gelen üyelerini çağırarak yeterlidir `ICalc1Contract` örneği oluşturucuya geçirilir ve sonuçlar döndürür. Bu sözleşme uyum sağlayan (`ICalc1Contract`) görünümüne (`ICalculator`).  
  
     Aşağıdaki kod, tamamlanan konak tarafı bağdaştırıcısı gösterir.  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. İsteğe bağlı olarak, Visual Studio çözümü oluşturun.  
  
## <a name="creating-the-host"></a>Konağı oluşturma  
 Bir ana bilgisayar uygulaması ile eklenti eklentisinin ana görünümünde aracılığıyla etkileşim kurar. Tarafından sağlanan eklentisi bulma ve etkinleştirme yöntemlerini kullanan <xref:System.AddIn.Hosting.AddInStore> ve <xref:System.AddIn.Hosting.AddInToken> sınıflar aşağıdakileri yapın:  
  
-   İşlem hattı ve eklenti bilgileri önbelleğini güncelleştirin.  
  
-   Ana görünüm türünün, eklentiler bulma `ICalculator`, belirtilen işlem hattı kök dizininin altındaki.  
  
-   Hangi kullanmak için eklenti belirtmek için kullanıcıdan.  
  
-   Seçili eklenti belirtilen güvenlik güven düzeyine sahip yeni bir uygulama etki alanında etkinleştirin.  
  
-   Özel çalıştırma `RunCalculator` yöntemi eklentinin ana görünümünde eklentisinin belirtildiği gibi yöntemleri çağırır.  
  
#### <a name="to-create-the-host"></a>Ana bilgisayar oluşturmak için  
  
1.  Adlı yeni bir proje ekleyin `Calc1Host` için `CalculatorV1` çözüm. Bu temel **konsol uygulaması** şablonu.  
  
2.  İçinde **Çözüm Gezgini**, System.AddIn.dll derlemeye bir başvuru ekleyin `Calc1Host` proje.  
  
3.  Bir proje başvurusu Ekle `Calc1HVA` proje. Proje başvurusu seçin ve **özellikleri** ayarlamak **Yereli Kopyala** için **False**. Visual Basic'teki **başvuruları** sekmesinde **proje özellikleri** ayarlanacak **Yereli Kopyala** için **False**.  
  
4.  Sınıf dosyasını (Visual Basic'te Modülü) Yeniden Adlandır `MathHost1`.  
  
5.  Visual Basic'teki **uygulama** sekmesinde **proje özellikleri** ayarlamak için iletişim kutusunun **Başlangıç nesnesi** için **Sub Main**.  
  
6.  Bir ad alanı başvuru sınıfı veya Modülü dosyasında ekleyin <xref:System.AddIn.Hosting>.  
  
7.  Eklentinin ana bilgisayar görünümü için bir ad alanı başvuru sınıfı veya modülü dosyasına ekleyin: `CalcHVAs`. (Visual Basic'te bu ad alanı başvurudur `Calc1HVA.CalcHVAs`sürece, Visual Basic projelerinde varsayılan ad alanlarını devre dışı bırakmış.)  
  
8.  İçinde **Çözüm Gezgini**, çözümü seçin ve **proje** menüsünde **özellikleri**. İçinde **çözüm özellik sayfaları** iletişim kutusu, kümesi **tek başlangıç projesi** bu ana bilgisayar uygulaması proje olacak.  
  
9. Sınıf veya modül dosyasında kullanmak <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> önbelleği güncelleştirmek için yöntemi. Kullanma <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> belirteçleri koleksiyonu almak ve kullanmak için yöntem <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> bir eklentiyi etkinleştirmek için yöntemi.  
  
     Aşağıdaki kod, tamamlanan Ana bilgisayar uygulaması gösterir.  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  Bu kod, işlem hattı klasör yapısını uygulama klasöründe bulunduğunu varsayar. Başka bir yerde bulunan ayarlar kod satırının tıklarsanız `addInRoot` değişken değişkeni içeren işlem hattı dizin yapınızı yolu.  
  
     Kod bir `ChooseCalculator` belirteçlerin listesi ve eklenti seçmek için kullanıcıdan istemek için yöntemi. `RunCalculator` Yöntemi basit matematik ifadeler için kullanıcıdan, kullanarak ifadeleri ayrıştırma `Parser` sınıfı ve sonuçları döndüren eklenti tarafından görüntüler.  
  
10. İsteğe bağlı olarak, Visual Studio çözümü oluşturun.  
  
## <a name="creating-the-add-in"></a>Eklentiyi oluşturma  
 Bir eklenti eklenti görünümü tarafından belirtilen yöntemleri uygular. Bu eklenti uygulayan `Add`, `Subtract`, `Multiply`, ve `Divide` işlemler ve ana bilgisayar sonuçları döndürür.  
  
#### <a name="to-create-the-add-in"></a>Eklenti oluşturmak için  
  
1.  Adlı yeni bir proje ekleyin `AddInCalcV1` için `CalculatorV1` çözüm. Bu temel **sınıf kitaplığı** şablonu.  
  
2.  İçinde **Çözüm Gezgini**, projeye System.AddIn.dll derlemesine bir başvuru ekleyin.  
  
3.  Bir proje başvurusu Ekle `Calc1AddInView` proje. Proje başvurusu seçin ve **özellikleri**ayarlayın **Yereli Kopyala** için **False**. Visual Basic'teki **başvuruları** sekmesinde **proje özellikleri** ayarlanacak **Yereli Kopyala** için **False** proje başvurusu için.  
  
4.  Sınıfı yeniden adlandırmak `AddInCalcV1`.  
  
5.  Sınıf dosyasında, bir ad alanı referansı eklemek <xref:System.AddIn> ve eklenti görünümü segment: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` Visual Basic'te).  
  
6.  Uygulama <xref:System.AddIn.AddInAttribute> özniteliğini `AddInCalcV1` sınıf bir eklenti olarak tanımlamak için sınıfı.  
  
7.  Olun `AddInCalcV1` sınıf uygulama eklenti görünümü temsil eden arabirim: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` Visual Basic'te).  
  
8.  Üyeleri uygulamak `ICalculator` uygun hesaplamaların sonuçlarını döndürerek.  
  
     Aşağıdaki kod, tamamlanan eklentisi gösterir.  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. İsteğe bağlı olarak, Visual Studio çözümü oluşturun.  
  
## <a name="deploying-the-pipeline"></a>İşlem hattı dağıtma  
 Derleme ve eklenti parçaları için gerekli işlem hattı dizin yapısını dağıtmak artık hazırsınız.  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a>Segment işlem hattına dağıtmak için  
  
1.  Çözümdeki her proje için kullanmak **derleme** sekmesinde **proje özellikleri** ( **derleme** Visual Basic sekmesini) değerini ayarlamak için **çıkış yolu**  ( **yapı çıkış yolu** Visual Basic'te). Uygulama klasörünüzdeki adlı `MyApp`, örneğin, projelerinizi aşağıdaki klasörler halinde oluşturmayı tercih:  
  
    |Proje|Yol|  
    |-------------|----------|  
    |AddInCalcV1|MyApp\Pipeline\AddIns\CalcV1|  
    |Calc1AddInSideAdapter|MyApp\Pipeline\AddInSideAdapters|  
    |Calc1AddInView|MyApp\Pipeline\AddInViews|  
    |Calc1Contract|MyApp\Pipeline\Contracts|  
    |Calc1Host|Uygulamam|  
    |Calc1HostSideAdapter|MyApp\Pipeline\HostSideAdapters|  
    |Calc1HVA|Uygulamam|  
  
    > [!NOTE]
    >  İşlem hattı klasör yapınız, uygulama klasörünüzdeki dışındaki bir konuma koymak karar verirseniz buna göre tabloda gösterilen yolları değiştirmeniz gerekir. İşlem hattı dizin gereksinimleri bkz [ardışık düzen geliştirme gereksinimleri](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
2.  Visual Studio çözümü oluşturun.  
  
3.  Derlemeler için doğru dizinleri kopyalanan ve hiçbir ek derlemeler kopyalarını yanlış klasörlerinde yüklenen emin olmak için uygulama ve işlem hattı dizinleri denetleyin.  
  
    > [!NOTE]
    >  Değişmedi, **Yereli Kopyala** için **False** için `Calc1AddInView` proje başvurusu `AddInCalcV1` proje, yükleyici bağlamı sorunları engeller eklenti bulunan öğesinden.  
  
     İşlem hattına dağıtma hakkında daha fazla bilgi için bkz: [ardışık düzen geliştirme gereksinimleri](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
## <a name="running-the-host-application"></a>Konak uygulama çalıştırma  
 Konak çalıştırın ve eklentisi ile etkileşim kurmak artık hazırsınız.  
  
#### <a name="to-run-the-host-application"></a>Ana bilgisayar uygulamasını çalıştırmak için  
  
1.  Komut isteminde, uygulama dizinine gidin ve ana bilgisayar uygulaması çalıştırın `Calc1Host.exe`.  
  
2.  Konak, tüm kullanılabilir eklentiler türüne bulur ve eklenti seçmenizi ister. Girin **1** için yalnızca eklenti.  
  
3.  Hesap makinesi için bir eşitlik girin; örn **2 + 2**. Sayılar ve işleci arasında boşluk olması gerekir.  
  
4.  Tür **çıkmak** basın **Enter** uygulamayı kapatmak için anahtar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Ana bilgisayarınız değiştiğinde geriye dönük uyumluluğu etkinleştirme](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [İzlenecek yol: Ana bilgisayarlar ve eklentiler arasında geçirme koleksiyonları](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [Ardışık Düzen geliştirme gereksinimleri](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [Sözleşmeler, görünümler ve bağdaştırıcılar](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [İşlem Hattı Geliştirme](../../../docs/framework/add-ins/pipeline-development.md)
