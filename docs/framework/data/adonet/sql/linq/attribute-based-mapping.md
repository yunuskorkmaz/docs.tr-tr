---
title: Öznitelik Tabanlı Eşleme
ms.date: 03/30/2017
ms.assetid: 6dd89999-f415-4d61-b8c8-237d23d7924e
ms.openlocfilehash: d7d7c14ca12e40af643d164069cf7b0f3165fa20
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223569"
---
# <a name="attribute-based-mapping"></a>Öznitelik Tabanlı Eşleme
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir SQL Server veritabanına eşleyen bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ya da uygulanan öznitelikleri veya bir dış eşleme dosyası kullanarak nesne modeli. Bu konuda, öznitelik tabanlı yaklaşım açıklanmaktadır.  
  
 En basit formunda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veritabanına eşleyen bir <xref:System.Data.Linq.DataContext>, bir sınıf, sütunları ve söz konusu sınıfın özelliklerini ilişkileri bir tablo. Öznitelikler, devralma hiyerarşisi, nesne modelinde eşlemek için de kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Visual Basic'de nesne modeli oluşturmak veya C# ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
 Genellikle Visual Studio kullanan geliştiricilerin kullanarak öznitelik tabanlı eşleme gerçekleştirmek [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. SQLMetal komut satırı aracını da kullanabilirsiniz veya elle kod öznitelikleri kendiniz yapabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Visual Basic'de nesne modeli oluşturmak veya C# ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
> [!NOTE]
>  Ayrıca, dış bir XML dosyası kullanarak da eşleştirebilirsiniz. Daha fazla bilgi için [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 Aşağıdaki bölümlerde öznitelik tabanlı eşleme daha ayrıntılı açıklanmaktadır. Daha fazla bilgi için <xref:System.Data.Linq.Mapping> ad alanı.  
  
## <a name="databaseattribute-attribute"></a>DatabaseAttribute özniteliği  
 Bu öznitelik, bir ad tarafından bağlantı sağlanamadığında veritabanının varsayılan adını belirtmek için kullanın. Bu öznitelik isteğe bağlıdır, ancak bunu kullanırsanız, uygulamalısınız <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> aşağıdaki tabloda açıklandığı gibi özellik.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|Dize|Bkz: <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|İle kullanılan kendi <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> özelliği, veritabanı adını belirtir.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.DatabaseAttribute>.  
  
## <a name="tableattribute-attribute"></a>TableAttribute özniteliği  
 Bu öznitelik, bir sınıf, bir veritabanı tablosu veya görünümü ile ilişkili bir varlık sınıfı olarak belirlemek için kullanın. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu öznitelik kalıcı sınıfları olan sınıflar değerlendirir. Aşağıdaki tabloda açıklanmıştır <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> özelliği.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>|Dize|Sınıf adı olarak aynı dize|Bir sınıf, bir veritabanı tablosu ile ilişkili bir varlık sınıfı olarak belirler.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
## <a name="columnattribute-attribute"></a>ColumnAttribute özniteliği  
 Bu öznitelik, bir veritabanı tablosundaki bir sütunu temsil etmek için bir varlık sınıfı üyesi belirtmek için kullanın. Bu öznitelik herhangi bir alan veya özellik uygulayabilirsiniz.  
  
 Yalnızca sütunları alınır ve kalıcı olarak tanımlamak üyeleri olduğunda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişiklikleri veritabanına kaydeder. Bu öznitelik olmadan üyeleri kalıcı olarak kabul edilir ve ekleme veya güncelleştirme için gönderilen değil.  
  
 Aşağıdaki tablo bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>|AutoSync|hiçbir zaman|Ortak dil çalışma zamanı (CLR) değerini almak için INSERT nebo update işleminden sonra bildirir.<br /><br /> Seçenekler: Her zaman, hiçbir zaman, in, eklerken.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>|Boole değeri|`true`|Bir sütunu null değerler içerebilir gösterir.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>|Dize|Çıkarsanan veritabanı sütun türü|Veritabanı türü ve değiştiriciler veritabanı sütununun türünü belirtmek için kullanır.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>|Dize|boş|Hesaplanan sütun, bir veritabanında tanımlar.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>|Boole değeri|`false`|Bir sütun veritabanı otomatik oluşturur değerleri içerdiğini gösterir.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>|Boole değeri|`false`|Sütun için bir ayrıştırıcı değeri içerdiğini gösterir bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Devralma Hiyerarşisi.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>|Boole değeri|`false`|Bu sınıf üyesi veya tablonun birincil anahtarlar bir parçası olan bir sütunu temsil ettiğini belirtir.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>|Boole değeri|`false`|Üyenin sütun türü, bir veritabanı zaman damgası veya sürüm numarası tanımlar.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>|UpdateCheck|`Always`, sürece <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> olduğu `true` bir üye|Belirtir nasıl [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iyimser eşzamanlılık çakışmaları algılama yaklaşıyor.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
> [!NOTE]
>  AssociationAttribute ve ColumnAttribute depolama özellik değerleri büyük/küçük harfe duyarlıdır. Örneğin, öznitelik AssociationAttribute.Storage özelliği için kullanılan değerleri başka bir yerde kod içinde kullanılan karşılık gelen özellik adları durum eşleştiğinden emin olun. Bu, tüm .NET programlama dillerinde, olanlar genellikle büyük Visual Basic dahil olmak üzere küçük harf duyarlı, olmayan geçerlidir. Depolama özelliği hakkında daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="associationattribute-attribute"></a>AssociationAttribute özniteliği  
 Bu öznitelik, birincil anahtar ilişkisi için yabancı anahtar gibi veritabanındaki ilişkiyi temsil etmek için bir özellik atamak için kullanın. İlişkiler hakkında daha fazla bilgi için bkz. [nasıl yapılır: Veritabanı ilişkileri eşleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md).  
  
 Aşağıdaki tablo bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteOnNull%2A>|Boole değeri|`false`|İlişkilendirme olarak ayarlandığında, yabancı anahtar üyeleri olan tüm NULL olmayan bir ilişkinin üzerinde yerleştirildiğinde, nesneyi siler null.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteRule%2A>|Dize|None|Silme davranışını ilişkisi ekler.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsForeignKey%2A>|Boole değeri|`false`|TRUE ise, üye yabancı anahtar veritabanı ilişkisini gösteren bir ilişkilendirme olarak belirler.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsUnique%2A>|Boole değeri|`false`|TRUE ise bir yabancı anahtar benzersizlik kısıtlamasını gösterir.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A>|Dize|İlgili sınıf kimliği|Bir veya daha fazla hedef varlık sınıfı üyeleri ilişkisinin diğer tarafındaki anahtar değerler olarak belirler.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.ThisKey%2A>|Dize|İçerilen sınıf kimliği|Bu varlık sınıfı üyeleri Birliği'nin bu tarafında anahtar değerlerini temsil edecek şekilde belirler.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.AssociationAttribute>.  
  
> [!NOTE]
>  AssociationAttribute ve ColumnAttribute depolama özellik değerleri büyük/küçük harfe duyarlıdır. Örneğin, öznitelik AssociationAttribute.Storage özelliği için kullanılan değerleri başka bir yerde kod içinde kullanılan karşılık gelen özellik adları durum eşleştiğinden emin olun. Bu, tüm .NET programlama dillerinde, olanlar genellikle büyük Visual Basic dahil olmak üzere küçük harf duyarlı, olmayan geçerlidir. Depolama özelliği hakkında daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="inheritancemappingattribute-attribute"></a>InheritanceMappingAttribute özniteliği  
 Bu öznitelik, bir devralma hiyerarşisi eşlemek için kullanın.  
  
 Aşağıdaki tablo bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>|Dize|Yok. Değer sağlanmalıdır.|Ayrıştırıcı kodu değerini belirtir.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>|Boole değeri|`false`|Hiçbir ayrıştırıcı değeri deposunda belirtilen değerlerden biri eşleştiğinde true ise bu türdeki bir nesne örneği oluşturur.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>|Tür|Yok. Değer sağlanmalıdır.|Hiyerarşi içinde sınıf türünü belirtir.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>.  
  
## <a name="functionattribute-attribute"></a>FunctionAttribute özniteliği  
 Bu öznitelik, bir yöntemi temsil eden, bir saklı yordam veya kullanıcı tanımlı işlev veritabanında olarak belirtmek için kullanın.  
  
 Aşağıdaki tabloda, bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A>|Boole değeri|`false`|False ise bir saklı yordam eşlemesi gösterir. TRUE ise, kullanıcı tanımlı bir işlev eşlemesi gösterir.|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.Name%2A>|Dize|Veritabanı adı olarak aynı dize|Saklı yordam veya kullanıcı tanımlı işlevin adını belirtir.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.FunctionAttribute>.  
  
## <a name="parameterattribute-attribute"></a>ParameterAttribute özniteliği  
 Bu öznitelik, saklı yordam yöntemlerde giriş parametrelerini eşlemek için kullanın.  
  
 Aşağıdaki tablo bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.DbType%2A>|Dize|Yok.|Veritabanı türü belirtir.|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.Name%2A>|Dize|Aynı dize olarak parametre adı veritabanında|Parametre için bir ad belirtir.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ParameterAttribute>.  
  
## <a name="resulttypeattribute-attribute"></a>ResultTypeAttribute özniteliği  
 Bu öznitelik, bir sonuç türü belirtmek için kullanın.  
  
 Aşağıdaki tablo bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ResultTypeAttribute.Type%2A>|Tür|(Hiçbiri)|Döndüren saklı yordamlarla eşlenen yöntemlerinde kullanılan <xref:System.Data.Linq.IMultipleResults>. Saklı yordam için geçerli veya beklenen türde eşlemeler bildirir.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ResultTypeAttribute>.  
  
## <a name="dataattribute-attribute"></a>DataAttribute özniteliği  
 Bu öznitelik adları ve özel depolama alanları belirtmek için kullanın.  
  
 Aşağıdaki tablo bu öznitelik özelliklerini açıklar.  
  
|Özellik|Tür|Varsayılan|Açıklama|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Name%2A>|Dize|Veritabanı adı ile aynı|Tablo, sütun ve benzeri adını belirtir.|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>|Dize|Ortak erişimciler|Temel alınan depolama alanı adını belirtir.|  
  
 Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.DataAttribute>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
