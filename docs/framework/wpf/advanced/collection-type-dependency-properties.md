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
ms.openlocfilehash: 71c29cc6d1c7955b889a56b0a6629690a2947c78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540361"
---
# <a name="collection-type-dependency-properties"></a>Koleksiyon Türü Bağımlılık Özellikleri
Bu konu, kılavuz ve nasıl özellik türü bir koleksiyon türü olduğu bir bağımlılık özelliği uygulamak önerilen modeller sağlar.  
  
 
  
<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>Bir koleksiyon türü bağımlılık özelliği uygulama  
 Genel olarak, bir bağımlılık özelliği için belirlediğiniz takip ettiğiniz uygulama modeli olan bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] burada bu özellik tarafından yedeklendiği özelliğinin sarmalayıcı bir <xref:System.Windows.DependencyProperty> tanımlayıcısı yerine bir alan veya diğer yapı. Bir koleksiyon türü özelliğini uygularken bu aynı düzeni uygular. Ancak, koleksiyonu içinde yer alan türü kendisi olduğunda bir koleksiyon türü özellik desenle karmaşıklık getirir bir <xref:System.Windows.DependencyObject> veya <xref:System.Windows.Freezable> türetilmiş sınıf.  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>Varsayılan değer dışında koleksiyon başlatma  
 Bağımlılık özelliği oluşturduğunuzda, özelliğin varsayılan değerini ilk alan değeri olarak belirtmeyin. Bunun yerine, bağımlılık özelliği meta verileri aracılığıyla varsayılan değeri belirtin. Bağımlılık özelliği meta verilerinde belirtilen varsayılan değeri, özellik bir başvuru türü ise, örneği başına varsayılan bir değer değil; Bunun yerine bu türünün tüm örnekleri için geçerli bir varsayılan değerdir. Bu nedenle yeni oluşturulan örneklerinin çalışan varsayılan değer olarak koleksiyon özelliği meta verileri tarafından tanımlanan tekil statik koleksiyonu kullanmamayı dikkatli olmanız gerekir. Bunun yerine, kasıtlı olarak koleksiyon değeri benzersiz (örnek) koleksiyonuna sınıf oluşturucu mantığının parçası olarak ayarladığınız emin olmanız gerekir. Aksi halde istemeden singleton sınıfı oluşturulmuş.  
  
 Aşağıdaki örnek göz önünde bulundurun. Aşağıdaki bölümde örneğin bir sınıf tanımını gösterir `Aquarium`. Koleksiyon türü bağımlılık özelliği sınıfı tanımlayan `AquariumObjects`, genel kullanan <xref:System.Collections.Generic.List%601> ile yazın bir <xref:System.Windows.FrameworkElement> tür kısıtlaması. İçinde <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> çağrısı bağımlılık özelliği, meta verileri için yeni bir genel varsayılan değer kurar <xref:System.Collections.Generic.List%601>.  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Ancak, yalnızca kod gösterildiği gibi bıraktığınız ise, o tek liste varsayılan değeri tüm örnekleri için paylaşılır `Aquarium`. İki ayrı nasıl ekleneceğini göstermek için tasarlanmıştır aşağıdaki test kodunu çalıştırdıysanız `Aquarium` örnekleri ve farklı bir tek `Fish` her biri için bir şaşırtıcı sonucu görürsünüz:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Bir sayısına sahip her koleksiyon yerine, her bir koleksiyon iki sayısına sahip değil! Bunun nedeni, her `Aquarium` eklenen kendi `Fish` varsayılan değer koleksiyonuna meta verilerde tek Oluşturucusu çağrısından sonuçlandı ve bu nedenle tüm örnekleri arasında paylaşılır. Bu neredeyse hiçbir zaman istediğiniz durumdur.  
  
 Bu sorunu düzeltmek için sınıf oluşturucu çağrısı bir parçası olarak benzersiz bir örnek için koleksiyon bağımlılık özelliği değeri sıfırlamanız gerekir. Özelliği salt okunur bağımlılık özelliği olduğundan, kullandığınız <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> yöntemi kullanarak ayarlamak için <xref:System.Windows.DependencyPropertyKey> , yalnızca sınıf içinde erişilebilir.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Şimdi, beklenen sonuçları görmek aynı kodu yeniden test çalıştırdıysanız, burada her `Aquarium` kendi benzersiz koleksiyonu desteklenmez.  
  
 Okuma-yazma, koleksiyon özelliği seçtiyseniz, bu deseni küçük bir değişim olacaktır. Bu durumda, ortak bir set erişimcisine hala anahtarı olmayan imzası çağırma başlatma yapmak için oluşturucudan çağırabilirsiniz <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> küme kapsayıcısı içinde bir ortak kullanarak <xref:System.Windows.DependencyProperty> tanımlayıcısı.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Derleme özelliklerinden bağlama değer değişikliklerini raporlama  
 Kendisini bir bağımlılık özelliği olan bir koleksiyon özelliği alt özelliklerine değişiklikleri otomatik olarak bildirmiyor. Derlemeye bağlamalar oluşturuyorsanız, bu nedenle bazı veri bağlama senaryoları geçersiz kılmalarını değişiklikleri, raporlama bağlama engelleyebilir. Ancak, koleksiyon türü kullanıyorsanız <xref:System.Windows.FreezableCollection%601> , koleksiyon türü olarak sonra koleksiyondaki içerilen öğelerin alt değişiklikler düzgün bildirilir ve bağlama beklendiği gibi çalışır.  
  
 Bağımlılık nesne koleksiyonundaki alt bağlama etkinleştirmek için koleksiyon özelliği türü olarak oluşturun <xref:System.Windows.FreezableCollection%601>, o koleksiyona herhangi bir tür kısıtlamasıyla <xref:System.Windows.DependencyObject> türetilmiş sınıf.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FreezableCollection%601>  
 [WPF için XAML ve Özel Sınıflar](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Bağımlılık Özelliği Meta Verisi](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)
