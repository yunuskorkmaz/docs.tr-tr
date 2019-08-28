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
ms.openlocfilehash: 9f102b584d2ed0b5a9d2bbb0e7ce3f7871ec40b2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046366"
---
# <a name="interfaces-related-to-data-binding"></a>Veri Bağlama ile İlgili Arabirimler

ADO.NET ile uygulamanızın bağlama ihtiyaçlarını ve çalıştığınız verileri karşılamak için birçok farklı veri yapısı oluşturabilirsiniz. Windows Forms verileri sağlayan veya tüketen kendi sınıflarınızı oluşturmak isteyebilirsiniz. Bu nesneler, temel veri bağlamasından, veri üzerinde yapılan değişikliklerin yapılandırılmış bir geri alma işlemi için tasarım zamanı desteği, hata denetimi, değişiklik bildirimi veya hatta destek sağlama gibi çeşitli işlev ve karmaşıklık düzeyleri sunabilir.

## <a name="consumers-of-data-binding-interfaces"></a>Veri bağlama arabirimlerinin tüketicileri

Aşağıdaki bölümlerde iki arabirim nesnesi grubu açıklanır. İlk grup, veri kaynağı yazarları tarafından veri kaynaklarına uygulanan arabirimleri listeler. Bu arabirimler, çoğu durumda denetim veya bileşen Windows Forms olan veri kaynağı tüketicileri tarafından kullanılmak üzere tasarlanmıştır. İkinci grup, bileşen yazarları tarafından kullanılmak üzere tasarlanan arabirimleri listeler. Bileşen yazarları, Windows Forms veri bağlama altyapısı tarafından tüketilen veri bağlamayı destekleyen bir bileşen oluştururken bu arabirimleri kullanır. Veri bağlamayı etkinleştirmek için bu arabirimleri, formunuz ile ilişkili sınıflar içinde uygulayabilirsiniz; Her örnek, verilerle etkileşimi sağlayan bir arabirim uygulayan bir sınıf gösterir. Visual Studio hızlı uygulama geliştirme (RAD) veri tasarımı deneyimi araçları bu işlevden zaten faydalanır.

### <a name="interfaces-for-implementation-by-data-source-authors"></a>Veri kaynağı yazarları tarafından uygulama için arabirimler

Aşağıdaki arabirimler Windows Forms denetimleri tarafından kullanılmak üzere tasarlanmıştır:

- <xref:System.Collections.IList>arayüz

  <xref:System.Collections.IList> Arabirimini uygulayan bir sınıf <xref:System.Array>, <xref:System.Collections.ArrayList>veya <xref:System.Collections.CollectionBase>olabilir. Bunlar türündeki <xref:System.Object>öğelerin dizinli listeleridir. Dizinin ilk öğesi türü belirlerken, bu listeler hogenou türleri içermelidir. <xref:System.Collections.IList>yalnızca çalışma zamanında bağlama için kullanılabilir olacaktır.

  > [!NOTE]
  > Windows Forms ile bağlama için iş nesnelerinin bir listesini oluşturmak istiyorsanız, ' yi kullanmayı göz önünde bulundurmanız <xref:System.ComponentModel.BindingList%601>gerekir. , <xref:System.ComponentModel.BindingList%601> İki yönlü Windows Forms veri bağlama için gereken birincil arabirimleri uygulayan genişletilebilir bir sınıftır.

- <xref:System.ComponentModel.IBindingList>arayüz

  Arabirimini uygulayan bir sınıf, <xref:System.ComponentModel.IBindingList> veri bağlama işlevlerinin çok daha yüksek bir düzeyini sağlar. Bu uygulama, liste öğelerinin değiştiği (örneğin, bir müşteri listesindeki üçüncü öğe, adres alanına bir değişikliğe sahip olduğu) ve listenin kendisinin ne zaman değiştiği (örneğin, Listedeki öğelerin sayısı artar veya azalır). Aynı verilere bağımlı birden fazla denetim olmasını planlıyorsanız ve denetimlerden birinde yapılan veri değişikliklerinin diğer bağlantılı denetimlere yayılması durumunda değişiklik bildirimi önemlidir.

  > [!NOTE]
  > Değişiklik bildirimi, <xref:System.ComponentModel.IBindingList> arabirim için etkin olan <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> özelliği aracılığıyla etkinleştirilir ve bu `true`, listenin değiştiğini veya <xref:System.ComponentModel.IBindingList.ListChanged> listedeki bir öğenin değiştiğini belirten bir olay oluşturur.

  Değişikliğin türü, <xref:System.ComponentModel.ListChangedType> <xref:System.ComponentModel.ListChangedEventArgs> parametresinin özelliği tarafından açıklanmıştır. Bu nedenle, veri modeli güncelleştirildiğinde aynı veri kaynağına bağlı diğer denetimler gibi bağımlı görünümler de güncelleştirilir. Bununla birlikte, listede yer alan nesneler, listenin <xref:System.ComponentModel.IBindingList.ListChanged> olayı yükseltebilmesi için, değiştiğinde listeyi bilgilendirmek zorunda kalır.

  > [!NOTE]
  > , <xref:System.ComponentModel.BindingList%601> <xref:System.ComponentModel.IBindingList> Arabirimin genel bir uygulamasını sağlar.

- <xref:System.ComponentModel.IBindingListView>arayüz

  <xref:System.ComponentModel.IBindingListView> Arabirimini uygulayan bir sınıf <xref:System.ComponentModel.IBindingList>, uygulamasının tüm işlevlerini ve filtreleme ve gelişmiş sıralama işlevlerini sağlar. Bu uygulama, dize tabanlı filtreleme ve özellik tanımlayıcısı yön çiftleri ile birden çok sütunlu sıralama sağlar.

- <xref:System.ComponentModel.IEditableObject>arayüz

  Arabirimini uygulayan bir sınıf, <xref:System.ComponentModel.IEditableObject> nesne üzerinde yapılan değişiklikler kalıcı yapıldığında bir nesnenin denetimine izin verir. Bu uygulama <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, ve yöntemlerini, nesne üzerinde <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> yapılan değişiklikleri geri almanıza olanak sağlayan, ve yöntemlerini kullanıma sunlar. Aşağıda <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, ve<xref:System.ComponentModel.IEditableObject.CancelEdit%2A> yöntemlerinin çalışmasının kısa bir açıklaması ve verilere yapılan değişikliklerin olası bir geri alınmasını sağlamak için bir diğeri ile birlikte nasıl çalıştıkları hakkında kısa bir açıklama verilmiştir:

  - <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> Yöntemi, bir nesne üzerinde bir düzenleme başlangıcını işaret eder. Bu arabirimi uygulayan bir nesnenin, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> yöntem çağrıldığında güncelleştirmelerin atılabileceği bir şekilde, bu işlemi bir bütün olarak bir yöntemle depolaması gerekir. Veri bağlama Windows Forms, tek bir düzenleme işleminin <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> kapsamında birden çok kez çağrı yapabilirsiniz ( <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>örneğin <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> <xref:System.ComponentModel.IEditableObject.EndEdit%2A>,,,). Uygulamaları, ' nin daha önce çağrılmış <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> olup olmadığını takip <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> etmelidirvedahasonraöğesine<xref:System.ComponentModel.IEditableObject> yapılan çağrıları yoksayar. Bu yöntem birden çok kez çağrabileceğinden, sonraki çağrıların geri dönüşme durumunda olması önemlidir; diğer bir deyişle, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> sonraki çağrılar yapılan güncelleştirmeleri yok edebilir veya ilk <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> çağrıda kaydedilen verileri değiştirebilir.

  - Yöntemi, nesne şu anda düzenleme <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> modundaysa, temel alınan nesneye çağrıldıktan sonra tüm değişiklikleri iter. <xref:System.ComponentModel.IEditableObject.EndEdit%2A>

  - <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> Yöntemi, nesnesinde yapılan tüm değişiklikleri atar.

  <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> ,<xref:System.ComponentModel.IEditableObject.EndEdit%2A>Ve yöntemlerinin<xref:System.ComponentModel.IEditableObject.CancelEdit%2A> nasıl çalıştığı hakkında daha fazla bilgi için bkz. [verileri veritabanına geri kaydetme](/visualstudio/data-tools/save-data-back-to-the-database).

  Bu işlem veri işlevselliği kavramı <xref:System.Windows.Forms.DataGridView> denetim tarafından kullanılır.

- <xref:System.ComponentModel.ICancelAddNew>arayüz

  <xref:System.ComponentModel.ICancelAddNew> Arabirimi uygulayan bir sınıf genellikle <xref:System.ComponentModel.IBindingList> arabirimini uygular ve veri kaynağında <xref:System.ComponentModel.IBindingList.AddNew%2A> yöntemi ile yapılan bir ek geri alma olanağı sağlar. Veri kaynağınız <xref:System.ComponentModel.IBindingList> arabirimini uyguluyorsa, <xref:System.ComponentModel.ICancelAddNew> arabirimi de uygulamalıdır.

- <xref:System.ComponentModel.IDataErrorInfo>arayüz

  Arabirimi uygulayan bir sınıf, <xref:System.ComponentModel.IDataErrorInfo> nesnelerin bağlantılı denetimlere özel hata bilgileri sunmasını sağlar:

  - <xref:System.ComponentModel.IDataErrorInfo.Error%2A> Özelliği genel hata iletisi metni döndürür (örneğin, "bir hata oluştu").

  - Özelliği, sütundan belirli bir hata iletisiyle bir dize döndürür (örneğin, " `State` sütundaki değer geçersiz"). <xref:System.ComponentModel.IDataErrorInfo.Item%2A>

- <xref:System.Collections.IEnumerable>arayüz

  <xref:System.Collections.IEnumerable> Arabirimi uygulayan bir sınıf genellikle ASP.NET tarafından kullanılır. Bu arabirim için Windows Forms desteği yalnızca <xref:System.Windows.Forms.BindingSource> bileşeni aracılığıyla kullanılabilir.

  > [!NOTE]
  > Bileşen <xref:System.Windows.Forms.BindingSource> , bağlama amacıyla <xref:System.Collections.IEnumerable> tüm öğeleri ayrı bir listeye kopyalar.

- <xref:System.ComponentModel.ITypedList>arayüz

  <xref:System.ComponentModel.ITypedList> Arabirimini uygulayan bir koleksiyon sınıfı, bağlantılı denetime sunulan sırayı ve özellik kümesini denetleme olanağı sağlar.

  > [!NOTE]
  > <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> Yöntemini uyguladığınızda<xref:System.ComponentModel.PropertyDescriptor> ve dizi null olmadığında dizideki son giriş, başka bir öğe listesi olan List özelliğini açıklayan özellik tanımlayıcısı olacaktır.

- <xref:System.ComponentModel.ICustomTypeDescriptor>arayüz

  <xref:System.ComponentModel.ICustomTypeDescriptor> Arabirimini uygulayan bir sınıf kendisiyle ilgili dinamik bilgiler sağlar. Bu arabirim öğesine <xref:System.ComponentModel.ITypedList> benzerdir, ancak listeler yerine nesneler için kullanılır. Bu arabirim tarafından <xref:System.Data.DataRowView> , temel alınan satırların şemasını projeye eklemek için kullanılır. Basit bir uygulama <xref:System.ComponentModel.ICustomTypeDescriptor> <xref:System.ComponentModel.CustomTypeDescriptor> sınıfı tarafından sağlanır.

  > [!NOTE]
  > Uygulayan <xref:System.ComponentModel.ICustomTypeDescriptor>türlere tasarım zamanı bağlamayı desteklemek için, türü Ayrıca, form üzerinde bir örnek olarak <xref:System.ComponentModel.IComponent> uygulamanız ve var olmalıdır.

- <xref:System.ComponentModel.IListSource>arayüz

  Arabirimi uygulayan bir sınıf, <xref:System.ComponentModel.IListSource> listede olmayan nesneler üzerinde liste tabanlı bağlamayı sağlar. Yöntemi <xref:System.ComponentModel.IListSource.GetList%2A> , öğesinden devraldığı<xref:System.Collections.IList>bir nesneden bağlanabilir bir liste döndürmek için kullanılır. <xref:System.ComponentModel.IListSource> <xref:System.ComponentModel.IListSource><xref:System.Data.DataSet> sınıfı tarafından kullanılır.

- <xref:System.ComponentModel.IRaiseItemChangedEvents>arayüz

  <xref:System.ComponentModel.IRaiseItemChangedEvents> Arabirimi uygulayan bir sınıf, <xref:System.ComponentModel.IBindingList> arabirimi de uygulayan bağlanabilir bir listesidir. Bu arabirim, türünün <xref:System.ComponentModel.IBindingList.ListChanged> <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> özelliği aracılığıyla türünde <xref:System.ComponentModel.ListChangedType.ItemChanged> olayları harekete geçirmediğini göstermek için kullanılır.

  > [!NOTE]
  > Veri kaynağınız daha önce <xref:System.ComponentModel.IRaiseItemChangedEvents> açıklanan olay dönüşümünü listelemek için özelliği sağlıyorsa ve <xref:System.Windows.Forms.BindingSource> bileşeniyle etkileşime geçmek için öğesini uygulamanız gerekir. Aksi takdirde, <xref:System.Windows.Forms.BindingSource> olay dönüştürmeyi listelemek için özelliği de, daha yavaş performansa neden olur.

- <xref:System.ComponentModel.ISupportInitialize>arayüz

  Arabirimi uygulayan bir bileşen, <xref:System.ComponentModel.ISupportInitialize> özellikleri ayarlamak ve ortak bağımlı özellikleri başlatmak için toplu iyileştirmelerin avantajlarından yararlanır. İki <xref:System.ComponentModel.ISupportInitialize> yöntem içerir:

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A>nesne başlatmanın başlamasını bildirir.

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A>nesne başlatmasının tamamlantığına işaret eder.

- <xref:System.ComponentModel.ISupportInitializeNotification>arayüz

  <xref:System.ComponentModel.ISupportInitializeNotification> Arabirimini uygulayan bir bileşen de <xref:System.ComponentModel.ISupportInitialize> arabirimini uygular. Bu arabirim, başlatma işleminin tamamlandığını diğer <xref:System.ComponentModel.ISupportInitialize> bileşenlere bildirme olanağı sağlar. <xref:System.ComponentModel.ISupportInitializeNotification> Arabirim iki üye içerir:

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A>bileşenin başlatılmış `boolean` olup olmadığını gösteren bir değer döndürür.

  - <xref:System.ComponentModel.ISupportInitializeNotification.Initialized><xref:System.ComponentModel.ISupportInitialize.EndInit%2A> çağrıldığında gerçekleşir.

- <xref:System.ComponentModel.INotifyPropertyChanged>arayüz

  Bu arabirimi uygulayan bir sınıf, özellik değerlerinden herhangi biri değiştiğinde bir olayı başlatan türdür. Bu arabirim, bir denetimin her özelliği için bir değişiklik olayına sahip olan deseninin yerini alacak şekilde tasarlanmıştır. Bir iş nesnesi bir <xref:System.ComponentModel.BindingList%601>içinde kullanıldığında, <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulamalıdır ve BindingList\`1 olayları <xref:System.ComponentModel.BindingList%601.ListChanged> türündeki <xref:System.ComponentModel.ListChangedType.ItemChanged>olaylara dönüştürür <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> .

  > [!NOTE]
  > Değişiklik bildiriminin, ilişkili istemci ile bir veri kaynağı arasındaki bağlamada gerçekleşmesi için, bağlantılı veri kaynağı türü <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi uygulamalıdır (tercih edilen) veya bağlama türü için *PropertyName* `Changed` olayları sağlayabilirsiniz. Ancak bunu yapmanız gerekmez.

### <a name="interfaces-for-implementation-by-component-authors"></a>Bileşen yazarları tarafından uygulama için arabirimler

Aşağıdaki arabirimler Windows Forms veri bağlama motoru tarafından tüketimine yöneliktir:

- <xref:System.Windows.Forms.IBindableComponent>arayüz

  Bu arabirimi uygulayan bir sınıf, veri bağlamayı destekleyen denetim olmayan bir bileşendir. Bu sınıf, bu arabirimin <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> ve <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> özellikleri aracılığıyla bileşenin veri bağlamalarını ve bağlama bağlamını döndürür.

  > [!NOTE]
  > Bileşeniniz öğesinden <xref:System.Windows.Forms.Control>devralırsa, <xref:System.Windows.Forms.IBindableComponent> arabirimini uygulamanız gerekmez.

- <xref:System.Windows.Forms.ICurrencyManagerProvider>arayüz

  <xref:System.Windows.Forms.ICurrencyManagerProvider> Arabirimini uygulayan bir sınıf, bu bileşenle ilişkili bağlamaları yönetmek için kendi kendine <xref:System.Windows.Forms.CurrencyManager> sağlayan bir bileşendir. Özel <xref:System.Windows.Forms.CurrencyManager> erişimi, <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> özelliği tarafından sağlanır.

  > [!NOTE]
  > Devralan <xref:System.Windows.Forms.Control> bir sınıf, kendi <xref:System.Windows.Forms.Control.BindingContext%2A> özelliği aracılığıyla bağlamaları otomatik olarak yönetir, bu nedenle uygulamanız <xref:System.Windows.Forms.ICurrencyManagerProvider> gereken durumlar oldukça nadir olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve Windows Forms](data-binding-and-windows-forms.md)
- [Nasıl yapılır: Bir Windows formunda basit bağlantılı denetim oluşturma](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
