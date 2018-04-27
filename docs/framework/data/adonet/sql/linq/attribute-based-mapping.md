---
title: Öznitelik tabanlı eşleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dd89999-f415-4d61-b8c8-237d23d7924e
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 49969af962db9fb533ad316622af42104438be7d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="attribute-based-mapping"></a>Öznitelik tabanlı eşleme
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir SQL Server veritabanı için eşleşen bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli ya da uygulanan öznitelikleri veya bir dış eşleme dosyası kullanarak. Bu konu, öznitelik tabanlı yaklaşım özetler.  
  
 En temel formunda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir veritabanı için eşleşen bir <xref:System.Data.Linq.DataContext>, bir sınıf, sütunları ve ilişkileri bu sınıfların özellikleri için bir tablo. Nesne modelinde bir devralma hiyerarşisini eşlemek için öznitelikler de kullanabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: Visual Basic veya C# içinde nesne modeli oluşturmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
 Visual Studio genellikle kullanan geliştiriciler kullanarak öznitelik tabanlı eşleme gerçekleştirmek [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. SQLMetal komut satırı aracı da kullanabilir veya elle kod öznitelikleri kendiniz kullanabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: Visual Basic veya C# içinde nesne modeli oluşturmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
> [!NOTE]
>  Ayrıca, harici bir XML dosyasını kullanarak da eşleştirebilirsiniz. Daha fazla bilgi için bkz: [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 Aşağıdaki bölümlerde öznitelik tabanlı eşleme daha ayrıntılı açıklanmıştır. Daha fazla bilgi için bkz: <xref:System.Data.Linq.Mapping> ad alanı.  
  
## <a name="databaseattribute-attribute"></a>DatabaseAttribute özniteliği  
 Bu öznitelik, bir ad, bağlantı tarafından sağlanmayan zaman veritabanının varsayılan adını belirtmek için kullanın. Bu öznitelik isteğe bağlıdır, ancak kullanırsanız, uygulamalısınız <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> aşağıdaki tabloda açıklandığı gibi özelliği.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|Dize|Bkz: <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|İle kullanılan kendi <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> özelliği, veritabanı adını belirtir.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.DatabaseAttribute>.  
  
## <a name="tableattribute-attribute"></a>TableAttribute özniteliği  
 Bu öznitelik, bir veritabanı tablosu veya görünümü ile ilişkili bir varlık sınıfı olarak bir sınıf belirlemek için kullanın. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu öznitelik kalıcı sınıfları olan sınıfları değerlendirir. Aşağıdaki tabloda açıklanmaktadır <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> özelliği.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>|Dize|Sınıf adı olarak aynı dize|Bir sınıf, bir veritabanı tablosu ile ilişkilendirilmiş bir varlık sınıfı olarak belirler.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
## <a name="columnattribute-attribute"></a>ColumnAttribute özniteliği  
 Bu öznitelik, bir veritabanı tablosundaki bir sütunu temsil etmek için bir varlık sınıfı üyesi belirlemek için kullanın. Bu öznitelik, herhangi bir alan veya özellik uygulayabilirsiniz.  
  
 Yalnızca sütunların alınır ve kalıcı olarak tanımlamak üyeleri zaman [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişiklikleri veritabanına kaydeder. Bu özniteliği olmadan üyeleri kalıcı olarak kabul edilir ve ekler veya güncelleştirmeler için gönderilen değil.  
  
 Aşağıdaki tabloda, bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>|AutoSync|Hiçbir zaman|Ortak dil çalışma zamanı (CLR) değerini almak için bir ekleme veya güncelleştirme işlemi sonra bildirir.<br /><br /> Seçenekler: Her zaman, hiçbir zaman, in, eklerken.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>|Boole değeri|`true`|Bir sütunu null değerler içerebilir gösterir.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>|Dize|Çıkarsanan veritabanı sütun türü|Veritabanı türleri ve değiştiricileri veritabanı sütununun türünü belirtmek için kullanır.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>|Dize|boş|Hesaplanmış bir sütun bir veritabanında tanımlar.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>|Boole değeri|`false`|Bir sütun veritabanı otomatik oluşturur değerleri içerdiğini gösterir.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>|Boole değeri|`false`|Sütun için bir Ayrıştırıcıyı değer içerdiğini gösterir bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Devralma Hiyerarşisi.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>|Boole değeri|`false`|Bu sınıf üyesi veya birincil anahtarlar tablosunun parçası olan bir sütunu temsil ettiğini belirtir.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>|Boole değeri|`false`|Üyenin sütun türü veritabanı zaman damgası veya sürüm numarası tanımlar.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>|UpdateCheck|`Always`, sürece <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> olan `true` üyesi için|Belirtir nasıl [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iyimser eşzamanlılık çakışmalarını algılama yaklaşıyor.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
> [!NOTE]
>  AssociationAttribute ve ColumnAttribute depolama özellik değerleri büyük küçük harf duyarlıdır. Örneğin, öznitelikte AssociationAttribute.Storage özelliği için kullanılan değerler başka bir yerde kod içinde kullanılan karşılık gelen özellik adları söz konusu eşleştiğinden emin olun. Bu, tüm .NET programlama dili için olanlar genellikle büyük Visual Basic dahil olmak üzere küçük harf duyarlı, olmayan geçerlidir. Depo özelliği hakkında daha fazla bilgi için bkz: <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="associationattribute-attribute"></a>AssociationAttribute özniteliği  
 Bu öznitelik, bir ilişki veritabanındaki yabancı anahtarı için birincil anahtar ilişkisi gibi göstermek için bir özellik belirlemek için kullanın. İlişkiler hakkında daha fazla bilgi için bkz: [nasıl yapılır: eşleme veritabanı ilişkileri](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md).  
  
 Aşağıdaki tabloda, bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteOnNull%2A>|Boole değeri|`false`|İlişkilendirme ayarlandığında, yabancı anahtar üyeleri olan tüm null ilişkilendirme yerleştirildiğinde, nesneyi siler null.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteRule%2A>|Dize|Yok.|Silme davranışı ilişki ekler.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsForeignKey%2A>|Boole değeri|`false`|TRUE ise, bir veritabanı ilişkisi temsil eden bir ilişki yabancı anahtar olarak üye belirler.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsUnique%2A>|Boole değeri|`false`|TRUE ise, yabancı anahtar benzersizlik kısıtlamasını gösterir.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A>|Dize|İlgili sınıf kimliği|İlişkinin diğer taraftaki anahtar değerleri olarak hedef varlık sınıfı bir veya daha fazla üyesi belirler.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.ThisKey%2A>|Dize|İçeren sınıf kimliği|Bu varlık sınıfı üyeleri bu ilişkilendirmeyi tarafındaki anahtar değerlerini temsil edecek şekilde belirler.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.AssociationAttribute>.  
  
> [!NOTE]
>  AssociationAttribute ve ColumnAttribute depolama özellik değerleri büyük küçük harf duyarlıdır. Örneğin, öznitelikte AssociationAttribute.Storage özelliği için kullanılan değerler başka bir yerde kod içinde kullanılan karşılık gelen özellik adları söz konusu eşleştiğinden emin olun. Bu, tüm .NET programlama dili için olanlar genellikle büyük Visual Basic dahil olmak üzere küçük harf duyarlı, olmayan geçerlidir. Depo özelliği hakkında daha fazla bilgi için bkz: <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="inheritancemappingattribute-attribute"></a>InheritanceMappingAttribute özniteliği  
 Bu öznitelik, bir devralma hiyerarşisini eşlemek için kullanın.  
  
 Aşağıdaki tabloda, bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>|Dize|Yok. Değer sağlanmalıdır.|Ayrıştırıcı kodu değerini belirtir.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>|Boole değeri|`false`|Ayrıştırıcı değer deposunda belirtilen değerlerden biri eşleştiğinde true ise, bu tür bir nesne örneği oluşturur.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>|Tür|Yok. Değer sağlanmalıdır.|Hiyerarşi içinde sınıf türünü belirtir.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>.  
  
## <a name="functionattribute-attribute"></a>FunctionAttribute özniteliği  
 Bu öznitelik, bir saklı yordam veya kullanıcı tanımlı işlev veritabanındaki temsil eden olarak bir yöntem belirtmek için kullanın.  
  
 Aşağıdaki tabloda, bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A>|Boole değeri|`false`|Yanlışsa, bir saklı yordam için eşlemeyi gösterir. TRUE ise, kullanıcı tanımlı bir işlev eşleme gösterir.|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.Name%2A>|Dize|Veritabanı adı olarak aynı dize|Saklı yordam veya kullanıcı tanımlı işlev adını belirtir.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.FunctionAttribute>.  
  
## <a name="parameterattribute-attribute"></a>ParameterAttribute özniteliği  
 Saklı yordam yöntemleri giriş parametrelerine eşleştirmek için bu öznitelik kullanın.  
  
 Aşağıdaki tabloda, bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.DbType%2A>|Dize|Yok.|Veritabanı türünü belirtir.|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.Name%2A>|Dize|Aynı dize veritabanı parametre adı olarak|Parametresi için bir ad belirtir.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ParameterAttribute>.  
  
## <a name="resulttypeattribute-attribute"></a>ResultTypeAttribute özniteliği  
 Bu öznitelik, bir sonuç türü belirtmek için kullanın.  
  
 Aşağıdaki tabloda, bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ResultTypeAttribute.Type%2A>|Tür|(Hiçbiri)|Döndüren saklı yordamları eşlenen yöntemlerinde kullanılan <xref:System.Data.Linq.IMultipleResults>. Saklı yordam için geçerli veya beklenen tür eşlemeleri bildirir.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ResultTypeAttribute>.  
  
## <a name="dataattribute-attribute"></a>DataAttribute özniteliği  
 Bu öznitelik adları ve özel depolama alanları belirtmek için kullanın.  
  
 Aşağıdaki tabloda, bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Name%2A>|Dize|Veritabanı adı ile aynı|Tablo, sütun ve benzeri adını belirtir.|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>|Dize|Ortak erişimciler|Temel alınan depolama alanının adını belirtir.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.DataAttribute>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
