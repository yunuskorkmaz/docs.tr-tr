---
title: Veri Bağlama ile İlgili Arabirimler
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], data-binding interfaces
- INotifyPropertyChanged interface
- IBindingListView interface
- IList interface [Windows Forms], Windows Forms data binding
- IBindingList interface [Windows Forms], Windows Forms data binding
- interfaces [Windows Forms], Windows Forms data binding
- IEditableObject interface [Windows Forms], Windows Forms data binding
- data binding [Windows Forms], interfaces
- IDataErrorInfo interface [Windows Forms], Windows Forms data binding
ms.assetid: 14e49a2e-3e46-47ca-b491-70d546333277
ms.openlocfilehash: 6c4470b33977408fa4429d187dafd76241d0d9d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541852"
---
# <a name="interfaces-related-to-data-binding"></a>Veri Bağlama ile İlgili Arabirimler
İle [!INCLUDE[vstecado](../../../includes/vstecado-md.md)], uygulamanız ve çalıştığınız veri bağlama gereksinimlerine uyacak şekilde birçok farklı veri yapılarını oluşturabilirsiniz. Sağlayan veya Windows Forms'ta veri tüketen kendi sınıflarınızı oluşturmak isteyebilirsiniz. Bu nesneler verilerin kendisini yapılan değişikliklerin yapılandırılmış bir geri alma için tasarım zamanı desteği, hata denetimi, değişiklik bildirimi veya hatta desteği sağlamaya temel veri bağlamanın dışında işlevselliği ve karmaşıklık, değişen düzeylerde sunabilir.  
  
## <a name="consumers-of-data-binding-interfaces"></a>Veri bağlama arabirimleri tüketicileri  
 Aşağıdaki bölümlerde iki grup arabirimi nesnelerin açıklanmaktadır. İlk gruptan veri kaynaklarında veri kaynağı yazarlar tarafından uygulanan arabirimler listeler. Bu arabirimleri, çoğu Windows Forms denetimleri durumlarda veya bileşenleri olan veri kaynağı tüketiciler tarafından kullanılması için tasarlanmıştır. İkinci grup bileşen yazarlar tarafından kullanılmak üzere tasarlanmış arabirimlerini listeler. Windows Forms veri bağlama altyapısı tarafından kullanılacak veri bağlamayı destekleyen bir bileşeni oluştururken bu arabirimleri bileşen yazarlar kullanın. Veri bağlama etkinleştirmek için formla ilişkili sınıfları içinde bu arabirimleri uygulayabilirsiniz; her durumda verilerle etkileşimi sağlayan bir arabirim uygulayan bir sınıf gösterir. Visual Studio hızlı uygulama geliştirme (RAD) veri tasarım deneyimi Araçları zaten bu işlevselliği yararlanın.  
  
### <a name="interfaces-for-implementation-by-data-source-authors"></a>Uygulama veri kaynağı yazarlar tarafından arabirimleri  
 Aşağıdaki arabirimleri Windows Forms denetimleri tarafından kullanılması için tasarlanmıştır:  
  
-   <xref:System.Collections.IList> Arabirimi  
  
     Uygulayan bir sınıf <xref:System.Collections.IList> arabirimi olabilir bir <xref:System.Array>, <xref:System.Collections.ArrayList>, veya <xref:System.Collections.CollectionBase>. Bu türdeki öğeleri dizinli listeleridir <xref:System.Object>. Dizinin ilk öğesi türü belirlediğinden bu listeleri homojen türü içermelidir. <xref:System.Collections.IList> yalnızca çalışma zamanında bağlamak için kullanılabilir olacaktır.  
  
    > [!NOTE]
    >  Windows Forms ile bağlama için iş nesneleri listesini oluşturmak istiyorsanız, kullanmayı düşünmelisiniz <xref:System.ComponentModel.BindingList%601>. <xref:System.ComponentModel.BindingList%601> Çift yönlü Windows Forms veri bağlama için gerekli birincil arabirimlerini uygular genişletilebilir bir sınıftır.  
  
-   <xref:System.ComponentModel.IBindingList> Arabirimi  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.IBindingList> arabirimi bir çok daha yüksek düzeyde veri bağlama işlevselliği sağlar. Bu uygulama temel sıralama yetenekleri ve ne zaman değişikliği liste öğeleri için değişiklik bildirimi sunar (örneğin, üçüncü öğesi bir liste müşterilerin bir değişiklik için adres alanı var.), liste değiştiğinde yanı sıra (örneğin, liste öğelerinin sayısını artırır veya azaltır). Değişiklik bildirimi aynı veriye bağlı birden çok denetim sahip olmayı planladığınız ve denetimleri birinde diğer ilişkili denetimler yaymak için veri değişikliklerinin istiyorsanız önemlidir.  
  
    > [!NOTE]
    >  Değişiklik bildirimi için etkinleştirildi <xref:System.ComponentModel.IBindingList> aracılığıyla arabirim <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> özelliği hangi, ne zaman `true`, başlatır bir <xref:System.ComponentModel.IBindingList.ListChanged> değişti olayı, değiştirilen listesi veya listeden bir öğe gösteren.  
  
     Değişiklik türü tarafından açıklanan <xref:System.ComponentModel.ListChangedType> özelliği <xref:System.ComponentModel.ListChangedEventArgs> parametresi. Bu nedenle, veri modeli güncelleştirildiğinde, aynı veri kaynağına bağlı diğer denetimleri gibi bağımlı tüm görünümler de güncelleştirilir. Ancak, listenin içinde yer alan nesneleri listesi yükseltebilirsiniz böylece bunlar değiştirdiğinizde listeyi bildir gerekecek <xref:System.ComponentModel.IBindingList.ListChanged> olay.  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BindingList%601> Genel uygulamasını sağlar <xref:System.ComponentModel.IBindingList> arabirimi.  
  
-   <xref:System.ComponentModel.IBindingListView> Arabirimi  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.IBindingListView> arabirim uygulaması tüm işlevselliğini sağlar <xref:System.ComponentModel.IBindingList>de olarak filtreleme ve gelişmiş işlevselliği sıralama. Bu uygulama dize tabanlı filtreleme ve sıralama sütunlu özellik tanımlayıcısı yön çiftiyle sunar.  
  
-   <xref:System.ComponentModel.IEditableObject> Arabirimi  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.IEditableObject> arabirimi ne zaman bu nesnedeki değişiklikler kalıcı yapılan denetlemek bir nesne izin verir. Bu uygulama ortaya koymaktadır <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, ve <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> etkinleştirmeniz nesneye yapılan değişiklikleri geri almak yöntemleri. Aşağıdadır işlevleriyle kısa bir açıklama <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, ve <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> yöntemleri ve nasıl başka bir olası geri alma verilerde yapılan değişiklikleri etkinleştirmek için birlikte çalışır:  
  
    -   <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> Yöntemi bir düzen başlangıç nesneye işaret eder. Bu arabirimi uygulayan bir nesne sonra herhangi bir güncelleştirme depolamak gerekir <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> güncelleştirmeleri atılan şekilde yöntem çağrısı, <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> yöntemi çağrılır. Windows Forms bağlama verilerde çağırabilirsiniz <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> işlem tek bir kapsamı içinde birden çok kez Düzenle (örneğin, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>). Uygulamaları <xref:System.ComponentModel.IEditableObject> olup izlenmesi <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> zaten çağrılmış ve sonraki çağrılar Yoksay <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>. Bu yöntem birden fazla defa çağrılabilir olduğundan, yapılan sonraki çağrılar dönüşlüdür önemlidir; diğer bir deyişle, sonraki <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> çağrı yapıldı veya kaydedilmiş verileri değiştirmek güncelleştirmeleri destroy olamaz ilk <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> çağırın.  
  
    -   <xref:System.ComponentModel.IEditableObject.EndEdit%2A> Yöntemi iter bu yana değişiklikler <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> nesne şu anda düzenleme modunda ise temel alınan nesnede çağrıldı.  
  
    -   <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> Yöntemi nesneye yapılan tüm değişiklikleri atar.  
  
     Nasıl hakkında daha fazla bilgi için <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, ve <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> yöntemleri çalışma, bkz: [verileri veritabanına kaydetmek](/visualstudio/data-tools/save-data-back-to-the-database).  
  
     Bu işlem veri işlevlerini kavramı tarafından kullanılan <xref:System.Windows.Forms.DataGridView> denetim.  
  
-   <xref:System.ComponentModel.ICancelAddNew> Arabirimi  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.ICancelAddNew> genellikle arabirimini uygulayan <xref:System.ComponentModel.IBindingList> arabirim ve veri kaynağı ile yapılan bir toplama geri olanak tanır <xref:System.ComponentModel.IBindingList.AddNew%2A> yöntemi. Implements, veri kaynağı, <xref:System.ComponentModel.IBindingList> arabirimi, aynı zamanda sahip olmanız gereken, uygulama <xref:System.ComponentModel.ICancelAddNew> arabirimi.  
  
-   <xref:System.ComponentModel.IDataErrorInfo> Arabirimi  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.IDataErrorInfo> arabirimi bağlama denetimleri için özel hata bilgileri sunmak nesneleri sağlar:  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Error%2A> Özelliği genel hata iletisi metni döndürür (örneğin, "bir hata oluştu").  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Item%2A> Özelliği sütundan belirli hata iletisiyle bir dize döndürür (örneğin, "değeri `State` sütunu geçersiz").  
  
-   <xref:System.Collections.IEnumerable> Arabirimi  
  
     Uygulayan bir sınıf <xref:System.Collections.IEnumerable> arabirimi tarafından tüketilen genellikle [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]. Bu arabirim için Windows Forms desteği aracılığıyla kullanılabilen yalnızca <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource> Bileşen kopyalar tüm <xref:System.Collections.IEnumerable> bağlama amacıyla için ayrı bir liste öğeleri.  
  
-   <xref:System.ComponentModel.ITypedList> Arabirimi  
  
     Uygulayan koleksiyonları sınıf <xref:System.ComponentModel.ITypedList> arabirim sırası ve bağımlı denetimi kullanıma sunulan özellikler kümesini denetleme olanağı sağlar.  
  
    > [!NOTE]
    >  Ne zaman uygulamanız <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> yöntemi ve <xref:System.ComponentModel.PropertyDescriptor> dizi null değil, son giriş dizideki öğeler, başka bir listesidir liste özelliği açıklayan özellik tanımlayıcısı olacaktır.  
  
-   <xref:System.ComponentModel.ICustomTypeDescriptor> Arabirimi  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.ICustomTypeDescriptor> arabirimi kendisi hakkında dinamik bilgi sağlar. Bu arabirim benzer <xref:System.ComponentModel.ITypedList> ancak listeleri yerine nesneler için kullanılır. Bu arabirim tarafından kullanılan <xref:System.Data.DataRowView> satırlar şeması projeye. Basit bir uyarlamasını <xref:System.ComponentModel.ICustomTypeDescriptor> tarafından sağlanan <xref:System.ComponentModel.CustomTypeDescriptor> sınıfı.  
  
    > [!NOTE]
    >  Tasarım zamanı bağlama desteklemek için o uygulama türleri <xref:System.ComponentModel.ICustomTypeDescriptor>, türü de uygulamalıdır <xref:System.ComponentModel.IComponent> ve formdaki bir örneği olarak mevcuttur.  
  
-   <xref:System.ComponentModel.IListSource> Arabirimi  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.IListSource> arabirimi liste tabanlı bağlama listesi olmayan nesneler üzerinde sağlar. <xref:System.ComponentModel.IListSource.GetList%2A> Yöntemi <xref:System.ComponentModel.IListSource> öğesinden devralmıyor bir nesneden bağlanabilirse listesini döndürmek için kullanılan <xref:System.Collections.IList>. <xref:System.ComponentModel.IListSource> tarafından kullanılan <xref:System.Data.DataSet> sınıfı.  
  
-   <xref:System.ComponentModel.IRaiseItemChangedEvents> Arabirimi  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.IRaiseItemChangedEvents> arabirimi ayrıca uygulayan bir listedir bağlanabilirse <xref:System.ComponentModel.IBindingList> arabirimi. Bu arabirim türünüz başlatır, göstermek için kullanılan <xref:System.ComponentModel.IBindingList.ListChanged> türünde olayları <xref:System.ComponentModel.ListChangedType.ItemChanged> aracılığıyla kendi <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> özelliği.  
  
    > [!NOTE]
    >  Uygulamanız gerekir <xref:System.ComponentModel.IRaiseItemChangedEvents> veri kaynağınızı daha önce açıklanan listesi olay dönüştürme özelliği sağlar ve ile etkileşim <xref:System.Windows.Forms.BindingSource> bileşeni. Aksi takdirde, <xref:System.Windows.Forms.BindingSource> daha yavaş performansı listesi olay dönüştürme özelliğini de gerçekleştirir.  
  
-   <xref:System.ComponentModel.ISupportInitialize> Arabirimi  
  
     Arabirimini uygulayan bir bileşen <xref:System.ComponentModel.ISupportInitialize> arabirimi özelliklerini ayarlama ve ortak bağımlı özellikler başlatma için toplu iş en iyi duruma getirme avantajları alır. <xref:System.ComponentModel.ISupportInitialize> İki yöntem içerir:  
  
    -   <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> Bu nesne başlatma başlangıç işaret eder.  
  
    -   <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> Bu nesne başlatma tamamlıyor işaret eder.  
  
-   <xref:System.ComponentModel.ISupportInitializeNotification> Arabirimi  
  
     Arabirimini uygulayan bir bileşen <xref:System.ComponentModel.ISupportInitializeNotification> arabirim de uygulayan <xref:System.ComponentModel.ISupportInitialize> arabirimi. Bu arabirim, diğer bildirmek verir <xref:System.ComponentModel.ISupportInitialize> bileşenleri, başlatma işlemi tamamlandı. <xref:System.ComponentModel.ISupportInitializeNotification> Arabirimi iki üye içerir:  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> döndüren bir `boolean` bileşen başlatılmış olup olmadığını belirten değer.  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> oluşur zaman <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> olarak adlandırılır.  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged> Arabirimi  
  
     Bu arabirimi uygulayan bir sınıf özellik değerlerini değiştirmek gerçekleştiğinde bir olay başlatır bir türüdür. Bu arabirim, değişiklik olayı denetimi her bir özellik için sahip olma deseni değiştirmek için tasarlanmıştır. Kullanıldığında bir <xref:System.ComponentModel.BindingList%601>, bir iş nesnesi uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi ve BindingList\`1 Dönüştür <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olayları <xref:System.ComponentModel.BindingList%601.ListChanged> türünde olayları <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
    > [!NOTE]
    >  Değişikliği veri ile ilişkili bir istemci arasında bir bağlama gerçekleşmesi için bildirim kaynağı, bağlı veri kaynağı türü uygulamanız ya da gerekir <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi (önerilen) veya sağlayabilir *propertyName* `Changed` olayları bağlama türü, ancak her ikisi de yapmamalısınız.  
  
### <a name="interfaces-for-implementation-by-component-authors"></a>Uygulama bileşeni yazarlar tarafından arabirimleri  
 Aşağıdaki arabirimleri Windows Forms veri bağlama altyapısı tarafından tüketimi için tasarlanmıştır:  
  
-   <xref:System.Windows.Forms.IBindableComponent> Arabirimi  
  
     Bu arabirimi uygulayan bir sınıf, veri bağlamayı destekleyen bir denetim olmayan bileşenidir. Bu sınıf veri bağlamalar ve bağlama bağlamını bileşeninin döndürür <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> ve <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> bu arabirimin özellikleri.  
  
    > [!NOTE]
    >  Bileşeniniz devraldığı varsa <xref:System.Windows.Forms.Control>, uygulamanız gerekmez <xref:System.Windows.Forms.IBindableComponent> arabirimi.  
  
-   <xref:System.Windows.Forms.ICurrencyManagerProvider> Arabirimi  
  
     Uygulayan bir sınıf <xref:System.Windows.Forms.ICurrencyManagerProvider> arabirimi kendi sağlayan bir bileşenidir <xref:System.Windows.Forms.CurrencyManager> belirli bu bileşenle ilişkili bağlamaları yönetmek için. Özel erişim <xref:System.Windows.Forms.CurrencyManager> tarafından sağlanan <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> özelliği.  
  
    > [!NOTE]
    >  Öğesinden devralınan bir sınıf <xref:System.Windows.Forms.Control> bağlamaları ile otomatik olarak yönetir, <xref:System.Windows.Forms.Control.BindingContext%2A> özelliği, içinde ihtiyacınız uygulamak bunu durumlarda <xref:System.Windows.Forms.ICurrencyManagerProvider> oldukça nadir şunlardır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlama ve Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Nasıl yapılır: Bir Windows Formunda Basit Bağlantılı Denetim Oluşturma](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [Windows Forms Veri Bağlama](../../../docs/framework/winforms/windows-forms-data-binding.md)
