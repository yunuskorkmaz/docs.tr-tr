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
ms.openlocfilehash: 4e40f7ec1922cdf43e6a0b8f5734acaaeefbc514
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834586"
---
# <a name="interfaces-related-to-data-binding"></a>Veri Bağlama ile İlgili Arabirimler

ADO.NET ile uygulamanızın bağlama ihtiyaçlarını ve çalıştığınız verileri karşılamak için birçok farklı veri yapısı oluşturabilirsiniz. Windows Forms verileri sağlayan veya tüketen kendi sınıflarınızı oluşturmak isteyebilirsiniz. Bu nesneler, temel veri bağlamasından, veri üzerinde yapılan değişikliklerin yapılandırılmış bir geri alma işlemi için tasarım zamanı desteği, hata denetimi, değişiklik bildirimi veya hatta destek sağlama gibi çeşitli işlev ve karmaşıklık düzeyleri sunabilir.

## <a name="consumers-of-data-binding-interfaces"></a>Veri bağlama arabirimlerinin tüketicileri

Aşağıdaki bölümlerde, iki arabirim nesnesi grubu açıklanır. İlk grup, veri kaynağı yazarları tarafından veri kaynaklarına uygulanan arabirimleri listeler. Bu arabirimler, çoğu durumda denetim veya bileşen Windows Forms olan veri kaynağı tüketicileri tarafından kullanılmak üzere tasarlanmıştır. İkinci grup, bileşen yazarları tarafından kullanılmak üzere tasarlanan arabirimleri listeler. Bileşen yazarları, Windows Forms veri bağlama altyapısı tarafından tüketilen veri bağlamayı destekleyen bir bileşen oluştururken bu arabirimleri kullanır. Veri bağlamayı etkinleştirmek için bu arabirimleri, formunuz ile ilişkili sınıflar içinde uygulayabilirsiniz; Her örnek, verilerle etkileşimi sağlayan bir arabirim uygulayan bir sınıf gösterir. Visual Studio hızlı uygulama geliştirme (RAD) veri tasarımı deneyimi araçları bu işlevden zaten faydalanır.

### <a name="interfaces-for-implementation-by-data-source-authors"></a>Veri kaynağı yazarları tarafından uygulama için arabirimler

Aşağıdaki arabirimler Windows Forms denetimleri tarafından kullanılmak üzere tasarlanmıştır:

- <xref:System.Collections.IList> arabirimi

  @No__t-0 arabirimini uygulayan bir sınıf <xref:System.Array>, <xref:System.Collections.ArrayList> veya <xref:System.Collections.CollectionBase> olabilir. Bunlar <xref:System.Object> türündeki öğelerin dizinli listeleridir. Dizinin ilk öğesi türü belirlerken, bu listeler hogenou türleri içermelidir. <xref:System.Collections.IList> yalnızca çalışma zamanında bağlama için kullanılabilir.

  > [!NOTE]
  > Windows Forms ile bağlama için iş nesnelerinin bir listesini oluşturmak istiyorsanız, <xref:System.ComponentModel.BindingList%601> ' ı kullanmayı göz önünde bulundurmanız gerekir. @No__t-0, iki yönlü Windows Forms veri bağlama için gereken birincil arabirimleri uygulayan genişletilebilir bir sınıftır.

- <xref:System.ComponentModel.IBindingList> arabirimi

  @No__t-0 arabirimini uygulayan bir sınıf, veri bağlama işlevlerinin çok daha yüksek bir düzeyini sağlar. Bu uygulama, liste öğelerinin değiştiği (örneğin, bir müşteri listesindeki üçüncü öğe, adres alanına bir değişikliğe sahip olduğu) ve listenin kendisinin ne zaman değiştiği (örneğin, Listedeki öğelerin sayısı artar veya azalır). Aynı verilere bağımlı birden fazla denetim olmasını planlıyorsanız ve denetimlerden birinde yapılan veri değişikliklerinin diğer bağlantılı denetimlere yayılması durumunda değişiklik bildirimi önemlidir.

  > [!NOTE]
  > @No__t-0 arabirimi için değişiklik bildirimi etkinleştirilir <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> özelliği ile `true`, listenin değiştiğini veya listedeki bir öğenin değiştiğini belirten bir @no__t 3 olayı harekete geçirirse.

  Değişikliğin türü, <xref:System.ComponentModel.ListChangedEventArgs> parametresinin <xref:System.ComponentModel.ListChangedType> özelliği tarafından tanımlanır. Bu nedenle, veri modeli güncelleştirildiğinde aynı veri kaynağına bağlı diğer denetimler gibi bağımlı görünümler de güncelleştirilir. Ancak, listede yer alan nesneler, listenin <xref:System.ComponentModel.IBindingList.ListChanged> olayını yükseltebilmesi için, değiştiğinde listeyi bilgilendirmek zorunda kalır.

  > [!NOTE]
  > @No__t-0 <xref:System.ComponentModel.IBindingList> arabiriminin genel bir uygulamasını sağlar.

- <xref:System.ComponentModel.IBindingListView> arabirimi

  @No__t-0 arabirimini uygulayan bir sınıf, bir <xref:System.ComponentModel.IBindingList> uygulamasının tüm işlevlerini ve filtreleme ve gelişmiş sıralama işlevlerini sağlar. Bu uygulama, dize tabanlı filtreleme ve özellik tanımlayıcısı yön çiftleri ile birden çok sütunlu sıralama sağlar.

- <xref:System.ComponentModel.IEditableObject> arabirimi

  @No__t-0 arabirimini uygulayan bir sınıf, nesne üzerinde yapılan değişiklikler kalıcı yapıldığında bir nesnenin denetimine izin verir. Bu uygulama, nesne üzerinde yapılan değişiklikleri geri almanıza olanak sağlayan <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A> ve <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> yöntemlerini kullanıma sunlar. Aşağıda, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A> ve <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> yöntemlerinin ve bir diğeri ile birlikte nasıl çalıştıkları hakkında kısa bir açıklama verilmiştir:

  - @No__t-0 yöntemi bir nesne üzerinde bir düzenleme başlangıcını işaret eder. Bu arabirimi uygulayan bir nesnenin, <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> yöntemi çağrıldığında güncelleştirmelerin atılabileceği şekilde <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> yöntem çağrısından sonra tüm güncelleştirmeleri depolaması gerekir. Veri bağlama Windows Forms, tek bir düzenleme işleminin kapsamında (örneğin, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>) <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> ' ı birden çok kez çağırabilirsiniz. @No__t-0 ' ın uygulamaları, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> ' in zaten çağrıldığından ve <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> ' ye yönelik sonraki çağrıları yoksaymalıdır. Bu yöntem birden çok kez çağrabileceğinden, sonraki çağrıların geri dönüşme durumunda olması önemlidir; diğer bir deyişle, sonraki <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> çağrıları, yapılan güncelleştirmeleri yok edebilir veya ilk <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> çağrısında kaydedilen verileri değiştirebilir.

  - @No__t-0 yöntemi, nesne şu anda düzenleme modundaysa, temel alınan nesneye <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> çağrıldıktan sonra tüm değişiklikleri gönderir.

  - @No__t-0 yöntemi nesne üzerinde yapılan değişiklikleri atar.

  @No__t-0, <xref:System.ComponentModel.IEditableObject.EndEdit%2A> ve <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> yöntemlerinin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [verileri veritabanına geri kaydetme](/visualstudio/data-tools/save-data-back-to-the-database).

  Bu işlem veri işlevselliği kavramı <xref:System.Windows.Forms.DataGridView> denetimi tarafından kullanılır.

- <xref:System.ComponentModel.ICancelAddNew> arabirimi

  @No__t-0 arabirimini uygulayan bir sınıf genellikle <xref:System.ComponentModel.IBindingList> arabirimini uygular ve <xref:System.ComponentModel.IBindingList.AddNew%2A> yöntemiyle veri kaynağına yapılan bir ek geri alma olanağı sağlar. Veri kaynağınız <xref:System.ComponentModel.IBindingList> arabirimini uyguluyorsa, <xref:System.ComponentModel.ICancelAddNew> arabirimini de uygulamalıdır.

- <xref:System.ComponentModel.IDataErrorInfo> arabirimi

  @No__t-0 arabirimini uygulayan bir sınıf, nesnelerin bağlantılı denetimlere özel hata bilgileri sunmasını sağlar:

  - @No__t-0 özelliği genel hata iletisi metni döndürür (örneğin, "bir hata oluştu").

  - @No__t-0 özelliği sütundan belirli bir hata iletisiyle bir dize döndürür (örneğin, "`State` sütunundaki değer geçersiz").

- <xref:System.Collections.IEnumerable> arabirimi

  @No__t-0 arabirimini uygulayan bir sınıf genellikle ASP.NET tarafından kullanılır. Bu arabirim için Windows Forms desteği yalnızca <xref:System.Windows.Forms.BindingSource> bileşeni ile kullanılabilir.

  > [!NOTE]
  > @No__t-0 bileşeni, tüm <xref:System.Collections.IEnumerable> öğelerini bağlama amacıyla ayrı bir listeye kopyalar.

- <xref:System.ComponentModel.ITypedList> arabirimi

  @No__t-0 arabirimini uygulayan bir koleksiyonlar sınıfı, bağlantılı denetime sunulan sırayı ve özellik kümesini denetleme olanağı sağlar.

  > [!NOTE]
  > @No__t-0 yöntemini uyguladığınızda ve <xref:System.ComponentModel.PropertyDescriptor> dizisi null olmadığında dizideki son giriş, başka bir öğe listesi olan List özelliğini açıklayan özellik tanımlayıcısı olacaktır.

- <xref:System.ComponentModel.ICustomTypeDescriptor> arabirimi

  @No__t-0 arabirimini uygulayan bir sınıf kendisiyle ilgili dinamik bilgiler sağlar. Bu arabirim <xref:System.ComponentModel.ITypedList> ' a benzerdir, ancak listeler yerine nesneler için kullanılır. Bu arabirim, temel alınan satırların şemasını projeye <xref:System.Data.DataRowView> tarafından kullanılır. @No__t-0 ' ın basit bir uygulanması <xref:System.ComponentModel.CustomTypeDescriptor> sınıfı tarafından sağlanır.

  > [!NOTE]
  > @No__t-0 uygulayan türlere tasarım zamanı bağlamayı desteklemek için, tür Ayrıca, <xref:System.ComponentModel.IComponent> ' i de uygular ve formda bir örnek olarak var olmalıdır.

- <xref:System.ComponentModel.IListSource> arabirimi

  @No__t-0 arabirimini uygulayan bir sınıf, listede olmayan nesneler üzerinde liste tabanlı bağlamayı sağlar. @No__t-1 ' in <xref:System.ComponentModel.IListSource.GetList%2A> yöntemi, <xref:System.Collections.IList> ' den kalıtımla almayan bir nesneden bağlanabilir bir liste döndürmek için kullanılır. <xref:System.ComponentModel.IListSource> <xref:System.Data.DataSet> sınıfı tarafından kullanılır.

- <xref:System.ComponentModel.IRaiseItemChangedEvents> arabirimi

  @No__t-0 arabirimini uygulayan bir sınıf, <xref:System.ComponentModel.IBindingList> arabirimini de uygulayan bağlanabilir bir listesidir. Bu arabirim, türünün <xref:System.ComponentModel.ListChangedType.ItemChanged> türünde <xref:System.ComponentModel.IBindingList.ListChanged> olaylarını <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> özelliği aracılığıyla mi harekete geçirmediğini göstermek için kullanılır.

  > [!NOTE]
  > Veri kaynağınız daha önce açıklanan olay dönüşümünü listelemek için özelliği sağlıyorsa ve <xref:System.Windows.Forms.BindingSource> bileşeniyle etkileşime geçmek <xref:System.ComponentModel.IRaiseItemChangedEvents> ' yı uygulamalısınız. Aksi takdirde, <xref:System.Windows.Forms.BindingSource>, olay dönüştürmeyi listelemek için özelliği de gerçekleştirecek daha yavaş performans elde eder.

- <xref:System.ComponentModel.ISupportInitialize> arabirimi

  @No__t-0 arabirimini uygulayan bir bileşen, özellikleri ayarlamak ve ortak bağımlı özellikleri başlatmak için toplu iyileştirmelerin avantajlarından yararlanır. @No__t-0 iki yöntem içerir:

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A>, nesne başlatmanın başladığı sinyaldir.

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A>, nesne başlatmasının tamamlanmasının sona ermesini bildirir.

- <xref:System.ComponentModel.ISupportInitializeNotification> arabirimi

  @No__t-0 arabirimini uygulayan bir bileşen, <xref:System.ComponentModel.ISupportInitialize> arabirimini de uygular. Bu arabirim, başlatma işleminin tamamlandığını diğer <xref:System.ComponentModel.ISupportInitialize> bileşenlerine bildirim vermenize olanak tanır. @No__t-0 arabirimi iki üye içerir:

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A>, bileşenin başlatılıp başlatılmayacağını gösteren bir `boolean` değeri döndürür.

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> çağrıldığında <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> oluşur.

- <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi

  Bu arabirimi uygulayan bir sınıf, özellik değerlerinden herhangi biri değiştiğinde bir olayı başlatan türdür. Bu arabirim, bir denetimin her özelliği için bir değişiklik olayına sahip olan deseninin yerini alacak şekilde tasarlanmıştır. @No__t-0 ' da kullanıldığında, bir iş nesnesi <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulamalıdır ve BindingList @ no__t-21, @no__t 3 olayları <xref:System.ComponentModel.ListChangedType.ItemChanged> türündeki @no__t 4 olayına dönüştürür.

  > [!NOTE]
  > Değişiklik bildiriminin, ilişkili istemci ile veri kaynağı arasındaki bağlamada gerçekleşmesi için, bağlantılı veri kaynağı türü <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulamalıdır (tercih edilen) veya bağlama türü için *propertyName*`Changed` olay sağlayabilirsiniz, ancak siz her ikisi de kullanılmamalıdır.

### <a name="interfaces-for-implementation-by-component-authors"></a>Bileşen yazarları tarafından uygulama için arabirimler

Aşağıdaki arabirimler Windows Forms veri bağlama motoru tarafından tüketimine yöneliktir:

- <xref:System.Windows.Forms.IBindableComponent> arabirimi

  Bu arabirimi uygulayan bir sınıf, veri bağlamayı destekleyen denetim olmayan bir bileşendir. Bu sınıf, bu arabirimin <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> ve <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> özellikleri aracılığıyla bileşenin veri bağlamalarını ve bağlama bağlamını döndürür.

  > [!NOTE]
  > Bileşeniniz <xref:System.Windows.Forms.Control> ' dan devralırsa, <xref:System.Windows.Forms.IBindableComponent> arabirimini uygulamanız gerekmez.

- <xref:System.Windows.Forms.ICurrencyManagerProvider> arabirimi

  @No__t-0 arabirimini uygulayan bir sınıf, bu bileşenle ilişkili bağlamaları yönetmek için kendi <xref:System.Windows.Forms.CurrencyManager> sağlayan bir bileşendir. Özel @no__t erişim-0 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> özelliği tarafından sağlanır.

  > [!NOTE]
  > @No__t-0 ' dan devralan bir sınıf <xref:System.Windows.Forms.Control.BindingContext%2A> özelliği aracılığıyla bağlamaları otomatik olarak yönetir, bu nedenle <xref:System.Windows.Forms.ICurrencyManagerProvider> ' yi uygulamanız gereken durumlar oldukça nadir olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve Windows Forms](data-binding-and-windows-forms.md)
- [Nasıl yapılır: Bir Windows Formunda Basit Bağlantılı Denetim Oluşturma](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
