---
title: Koleksiyon Türü Bağımlılık Özellikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], dependency
- properties [WPF], collection-type
- dependency properties [WPF]
- collection-type properties [WPF]
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
ms.openlocfilehash: e783ce4b95b52b86671181dfe4b316d4b91d8fc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141545"
---
# <a name="collection-type-dependency-properties"></a>Koleksiyon Türü Bağımlılık Özellikleri
Bu konu, özellik türü bir koleksiyon türü olan bir bağımlılık özelliğinin nasıl uygulanacağı için kılavuz ve önerilen desenler sağlar.  

<a name="implementing"></a>
## <a name="implementing-a-collection-type-dependency-property"></a>Toplama Türü Bağımlılık Özelliği Uygulama  
 Genel olarak bir bağımlılık özelliği için, izlemeniz gereken uygulama deseni, bu özelliğin bir alan <xref:System.Windows.DependencyProperty> veya başka bir yapı yerine tanımlayıcı tarafından desteklenen bir CLR özellik sarıcı tanımlamanızdır. Bir koleksiyon türü özelliği uygularken aynı deseni izlersiniz. Ancak, koleksiyon türü özelliği, koleksiyon içinde bulunan tür kendisi bir <xref:System.Windows.DependencyObject> veya <xref:System.Windows.Freezable> türetilmiş sınıf olduğunda desen bazı karmaşıklık tanıtır.  
  
<a name="initializing"></a>
## <a name="initializing-the-collection-beyond-the-default-value"></a>Koleksiyonu Varsayılan Değerin Ötesinde Başlatma  
 Bağımlılık özelliği oluşturduğunuzda, özellik varsayılan değerini başlangıç alanı değeri olarak belirtmezsiniz. Bunun yerine, bağımlılık özelliği meta verileri aracılığıyla varsayılan değeri belirtirsiniz. Mülkünüz bir başvuru türüyse, bağımlılık özelliği meta verilerinde belirtilen varsayılan değer örnek başına varsayılan değer değildir; bunun yerine, türün tüm örnekleri için geçerli varsayılan bir değerdir. Bu nedenle, koleksiyon özelliği meta verileri tarafından tanımlanan tekil statik koleksiyonu, türün yeni oluşturulan örnekleri için çalışan varsayılan değer olarak kullanmamaya dikkat etmelisiniz. Bunun yerine, sınıf oluşturucu mantığınızın bir parçası olarak koleksiyon değerini kasıtlı olarak benzersiz (örnek) koleksiyona ayarladığınızdan emin olmalısınız. Aksi takdirde kasıtsız bir singleton sınıfı oluşturmuş olursunuz.  
  
 Aşağıdaki örneği inceleyin. Örneğin aşağıdaki bölümü varsayılan değeri olan `Aquarium`bir kusur içeren bir sınıf tanımını gösterir. Sınıf, <xref:System.Windows.FrameworkElement> tür kısıtlaması olan `AquariumObjects`genel <xref:System.Collections.Generic.List%601> türü kullanan koleksiyon türü bağımlılık özelliğini tanımlar. Bağımlılık <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> özelliği için çağrıda, meta veri varsayılan değeri yeni bir genel <xref:System.Collections.Generic.List%601>olarak belirler.

> [!WARNING]
> Aşağıdaki kod doğru şekilde çalışmaz.

 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Ancak, kodu gösterildiği gibi bıraktıysanız, bu tek liste varsayılan değeri `Aquarium`tüm örnekleri için paylaşılır. İki ayrı `Aquarium` örneği nasıl anında anladığınızı ve her birine nasıl farklı `Fish` bir tane ekleyeceğinizi göstermek amacıyla aşağıdaki test kodunu çalıştırdıysanız, şaşırtıcı bir sonuç görürsünüz:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Her koleksiyon bir sayıya sahip olmak yerine, her koleksiyonun sayısı ikidir! Bunun nedeni, `Aquarium` her `Fish` biri meta verilerdeki tek bir kurucu çağrısından kaynaklanan ve bu nedenle tüm örnekler arasında paylaşılan varsayılan değer koleksiyonuna kendininkini eklemesidir. Bu durum neredeyse hiçbir zaman istediğin şey değil.  
  
 Bu sorunu gidermek için, sınıf oluşturucu çağrısının bir parçası olarak koleksiyon bağımlılık özelliği değerini benzersiz bir örneye sıfırlamanız gerekir. Özellik salt okunur bağımlılık özelliği olduğundan, yalnızca <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> sınıf içinde erişilebilen <xref:System.Windows.DependencyPropertyKey> özelliği kullanarak onu ayarlamak için yöntemi kullanırsınız.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Şimdi, aynı test kodunu tekrar çalıştırdıysanız, her birinin `Aquarium` kendi benzersiz koleksiyonunu desteklediği daha beklenen sonuçları görebilirsiniz.  
  
 Eğer koleksiyon özelliği okuma-yazma için seçtiyseniz bu desen üzerinde küçük bir varyasyon olacaktır. Bu durumda, ortak tanımlayıcı kullanarak, <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> <xref:System.Windows.DependencyProperty> yine de set sarıcınızın anahtarsız imzasını çağıran başlatmayı yapmak için oluşturucudan ortak ayarlı erişimci çağırabilirsiniz.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Toplama Özelliklerinden Bağlayıcı Değer Değişikliklerini Bildirme  
 Kendisi bir bağımlılık özelliği olan bir toplama özelliği, alt özelliklerindeki değişiklikleri otomatik olarak bildirmez. Bir koleksiyona bağlama lar oluşturuyorsanız, bu durum bağlamanın değişiklikleri bildirmesini engelleyebilir ve bu nedenle bazı veri bağlama senaryolarını geçersiz kılabilir. Ancak, koleksiyon türünü <xref:System.Windows.FreezableCollection%601> koleksiyon türünüz olarak kullanırsanız, koleksiyonda bulunan öğelere alt özellik değişiklikleri düzgün şekilde bildirilir ve beklendiği gibi bağlama çalışmaları yapılır.  
  
 Bağımlılık nesnesi koleksiyonunda alt özellik bağlamayı etkinleştirmek <xref:System.Windows.FreezableCollection%601>için, türdeki herhangi <xref:System.Windows.DependencyObject> bir sınıfa bu koleksiyon için bir tür kısıtlaması olan tür olarak koleksiyon özelliğini oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FreezableCollection%601>
- [WPF için XAML ve Özel Sınıflar](xaml-and-custom-classes-for-wpf.md)
- [Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
