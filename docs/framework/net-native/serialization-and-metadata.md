---
title: Serileştirme ve Meta Veriler
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c82d32fe5b1e62a19ff5e2920c5943f1303b2d64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207038"
---
# <a name="serialization-and-metadata"></a>Serileştirme ve Meta Veriler
Uygulamanızı serileştirir ve nesneleri seri durumdan çıkarır, girişler için çalışma zamanı yönergeleri eklemeniz gerekebilir (. rd.xml) dosyasını gerekli meta verileri çalışma zamanında mevcut olduğundan emin olun. Seri hale getiricileri genişletme iki kategorisi vardır ve her çalışma zamanı yönergeleri dosyanızda farklı işleme gerektirir:  
  
-   Üçüncü taraf seri hale getiricileri genişletme yansıma tabanlı. Bu değişiklikler, çalışma zamanı yönergeleri dosyanıza gerektirir ve sonraki bölümde ele alınmıştır.  
  
-   Yansıma olmayan .NET Framework sınıf kitaplığında bulunan seri hale getiricileri genişletme temel. Bu değişiklikler, çalışma zamanı yönergeleri dosyanıza gerektirebilir ve ele alınmıştır [Microsoft seri hale getiricileri genişletme](#Microsoft) bölümü.  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a>Üçüncü taraf seri hale getiricileri genişletme  
 Yansıma tabanlı üçüncü bölümü seri hale getiricileri genişletme Newtonsoft.JSON, dahil, normal uygulanır. Serileştirilmiş veriler ikili büyük nesne (BLOB) göz önünde bulundurulduğunda, veri alanları hedef türünün alanları ada göre arayarak somut bir türde atanır. En azından bu kitaplıkları kullanarak neden [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) her biri için özel durumlar <xref:System.Type> serileştirmek veya de seri durumdan çalıştığınızda nesne bir `List<Type>` koleksiyonu.  
  
 Bu seri hale getiricileri genişletme meta veriler eksik neden sorunlarını gidermek için en kolay yolu, tek bir ad altında serileştirme sırasında kullanılan türleri toplamaktır (gibi `App.Models`) ve geçerli bir `Serialize` meta verileri yönergesine:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Örnekte kullanılan söz dizimi hakkında daha fazla bilgi için bkz: [ \<Namespace > öğesi](../../../docs/framework/net-native/namespace-element-net-native.md).  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a>Microsoft seri hale getiricileri genişletme  
 Ancak <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer> sınıfları yansıma kullanan değil, bunlar serileştirilecek veya seri durumdan için nesneye bağlı kod oluşturulmasını gerektirir. Her seri hale getirici için aşırı yüklü oluşturucular dahil bir <xref:System.Type> parametresi serileştirilecek veya seri durumdan türünü belirtir. Bu tür kodunuzda nasıl belirttiğiniz gerçekleştirmeniz gereken eylemi sonraki iki bölümde açıklandığı gibi tanımlar.  
  
### <a name="typeof-used-in-the-constructor"></a>typeof oluşturucuda kullanılır  
 Bu seri hale getirme sınıfların bir oluşturucuyu çağırmak ve dahil C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) anahtar sözcüğü, yöntem çağrısında **herhangi bir ek çalışma yapmak gerekmez**. Örneğin, her bir seri hale getirme sınıfı oluşturucusunu aşağıdaki çağrıları içinde `typeof` anahtar sözcüğü, oluşturucuya geçirilen ifade parçası olarak kullanılır.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Derleyici Bu kod otomatik olarak ele alacak.  
  
### <a name="typeof-used-outside-the-constructor"></a>typeof Oluşturucu dışında kullanılan  
 Bu seri hale getirme sınıfların bir oluşturucuyu çağırmak ve kullanmak C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) anahtar sözcüğü oluşturucunun sağlanan ifade dışında <xref:System.Type> parametresi, aşağıdaki kod, olduğu gibi [!INCLUDE[net_native](../../../includes/net-native-md.md)] derleyici tür çözümlenemiyor:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 Bu durumda, türü çalışma zamanı yönergeleri dosyasında şunun gibi bir giriş ekleyerek belirtmeniz gerekir:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Benzer şekilde, bir oluşturucu gibi çağırırsanız <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> ve bir dizi ek <xref:System.Type> , aşağıdaki kod olduğu gibi seri hale getirmek için nesneleri [!INCLUDE[net_native](../../../includes/net-native-md.md)] derleyici bu tür çözümleyemiyor.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Çalışma zamanı yönergeleri dosyasına girişleri her türü aşağıdaki gibi eklemeniz gerekir:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Örnekte kullanılan söz dizimi hakkında daha fazla bilgi için bkz: [ \<türü > öğesi](../../../docs/framework/net-native/type-element-net-native.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
- [\<Türü > öğesi](../../../docs/framework/net-native/type-element-net-native.md)
- [\<Namespace > öğesi](../../../docs/framework/net-native/namespace-element-net-native.md)
