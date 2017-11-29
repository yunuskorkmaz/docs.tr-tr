---
title: "Serileştirme ve Meta Veriler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e7216f14fb0b8da27b870fc8e66b24f6d87fcaad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="serialization-and-metadata"></a>Serileştirme ve Meta Veriler
Uygulamanızı serileştirir ve nesneleri seri durumdan çıkarır, çalışma zamanı yönergeleri girişleri eklemeniz gerekebilir (. rd.xml) dosyası gerekli meta veri çalışma zamanında mevcut olduğundan emin olun. Serileştiricileri iki kategorisi vardır ve her çalışma zamanı yönergeleri dosyanızda farklı işleme gerektirir:  
  
-   Yansıma tabanlı üçüncü taraf serileştiricileri. Bu çalışma zamanı yönergeleri dosyanıza değişiklikler gerektirir ve sonraki bölümde açıklanmıştır.  
  
-   .NET Framework Sınıf Kitaplığı'nda bulunan serileştiricileri olmayan yansıma tabanlı. Bu, çalışma zamanı yönergeleri dosyanızı değişiklikler gerektirebilir ve ele alınmıştır [Microsoft serileştiricileri](#Microsoft) bölümü.  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a>Üçüncü taraf serileştiricileri  
 Yansıma tabanlı üçüncü bölümü serileştiricileri Newtonsoft.JSON, dahil olmak üzere, genellikle. Serileştirilmiş veriler ikili büyük nesne (BLOB) göz önüne alındığında, veri alanları hedef türünün alanları ada göre arayarak somut bir türde atanır. Bu kitaplıklar kullanarak en az neden [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) her biri için özel durumlar <xref:System.Type> serileştirmek veya seri durumdan içinde çalıştığınızda nesne bir `List<Type>` koleksiyonu.  
  
 Eksik meta verileri ile bu serileştiricileri için neden olduğu sorunları gidermek için en kolay yolu, tek bir ad altında serileştirmede kullanılacak türleri toplamaktır (gibi `App.Models`) ve geçerli bir `Serialize` meta verileri yönergeye:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Örnekte kullanılan sözdizimi hakkında daha fazla bilgi için bkz: [ \<Namespace > öğesi](../../../docs/framework/net-native/namespace-element-net-native.md).  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a>Microsoft serileştiricileri  
 Ancak <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer> sınıfları yansıma bağlı değil, oluşturulacak kod serileştirilecek veya seri için seçtiğiniz nesneye bağlı duyarlar. Her seri hale getirici için aşırı yüklü oluşturucular içeren bir <xref:System.Type> serileştirilecek veya seri durumdan türünü belirten parametre. Bu tür kodunuzu nasıl belirttiğiniz gerçekleştirmesi gereken eylemi sonraki iki bölümde açıklandığı gibi tanımlar.  
  
### <a name="typeof-used-in-the-constructor"></a>typeof oluşturucuda kullanılır  
 Bu seri hale getirme sınıfların Oluşturucusu çağırın ve C# dahil [typeof](~/docs/csharp/language-reference/keywords/typeof.md) yöntem çağrısı bir anahtar sözcük **başka çalışma yapmak zorunda**. Örneğin, her bir seri hale getirme sınıf oluşturucu aşağıdaki çağrıları içinde `typeof` anahtar sözcüğü oluşturucuya geçirilen ifade parçası olarak kullanılır.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Derleyici otomatik olarak bu kodu işler.  
  
### <a name="typeof-used-outside-the-constructor"></a>typeof Oluşturucusu dışında kullanılan  
 Bu seri hale getirme sınıfların Oluşturucusu çağırın ve C# kullanan [typeof](~/docs/csharp/language-reference/keywords/typeof.md) anahtar sözcüğü oluşturucuya 's sağlanan ifade dışında <xref:System.Type> parametresi, aşağıdaki kod, olduğu gibi [!INCLUDE[net_native](../../../includes/net-native-md.md)] derleyici olamaz türü çözümlenemedi:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 Bu durumda, türü çalışma zamanı yönergeleri dosyasında şöyle bir giriş ekleyerek belirtmeniz gerekir:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Benzer şekilde, bir oluşturucu gibi çağırırsanız <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> ve bir dizi ek sağlamak <xref:System.Type> olduğu gibi aşağıdaki kod, serileştirilecek nesneleri [!INCLUDE[net_native](../../../includes/net-native-md.md)] derleyici, bu tür çözmek olamaz.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Çalışma zamanı yönergeleri dosyasına girişleri her türü aşağıdaki gibi eklemeniz gerekir:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Örnekte kullanılan sözdizimi hakkında daha fazla bilgi için bkz: [ \<türü > öğesi](../../../docs/framework/net-native/type-element-net-native.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma zamanı yönerge öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [\<Tür > öğesi](../../../docs/framework/net-native/type-element-net-native.md)  
 [\<Namespace > öğesi](../../../docs/framework/net-native/namespace-element-net-native.md)
