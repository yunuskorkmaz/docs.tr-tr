---
title: SqlMetal.exe (Kod Üretme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: d5b4c2b59b585b3d3a3584ef9055e70c9d998e85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71044085"
---
# <a name="sqlmetalexe-code-generation-tool"></a>SqlMetal.exe (Kod Üretme Aracı)
SqlMetal komut satırı aracı,.NET Framework [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] bileşeni için kod ve eşleme oluşturur. Bu konunun ilerisinde görünen seçenekleri uygulayarak, SqlMetal'den aşağıdakileri içeren çeşitli farklı eylemler gerçekleştirmesini isteyebilirsiniz:  
  
- Bir veritabanından, kaynak kodu ve eşleme öznitelikleri veya bir eşleme dosyası oluşturmak.  
  
- Bir veritabanından, dosya özelleştirme için bir ara veritabanı işaretleme dili (.dbml) dosyası oluşturmak.  
  
- Bir .dbml dosyasından, kod veya eşleme öznitelikleri veya bir eşleme dosyası üretmek.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Varsayılan olarak, dosya :\Program Files\Microsoft `drive`SDKs\Windows\v`n.nn`\bin adresinde bulunur. Visual Studio'yu yüklemezseniz, [Windows SDK'yı](https://go.microsoft.com/fwlink/?LinkId=142225)indirerek SQLMetal dosyasını da alabilirsiniz.  
  
> [!NOTE]
> Visual Studio kullanan geliştiriciler, varlık sınıfları oluşturmak için Object İlişkisel Tasarımcı'yı da kullanabilir. Komut satırı yaklaşımı, büyük veritabanları için uygun düşmektedir. SqlMetal bir komut satırı aracı olduğundan, bir oluşturma işleminde kullanabilirsiniz.  
  
 To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın. Komut isteminde aşağıdakileri yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a>Seçenekler  
 En güncel seçenek listesini görüntülemek `sqlmetal /?` için, yüklenen konumdan komut istemine yazın.  
  
 **Bağlantı Seçenekleri**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/server:** * \<isim>*|Veritabanı sunucusu adını belirtir.|  
|**/database:** * \<isim>*|Sunucuda veritabanı kataloğu belirtir.|  
|**/kullanıcı:** * \<isim>*|Oturum açma kullanıcı kimliğini belirtir. Varsayılan değer: Windows kimlik doğrulamasını kullanın.|  
|**/password:** * \<şifre>*|Oturum açma parolasını belirtir. Varsayılan değer: Windows kimlik doğrulaması kullan.|  
|**/conn:** * \<bağlantı dizesi>*|Veritabanı bağlantısı dizesi belirtir. **/server**, /database , **/user**, veya **/password** seçenekleri yle kullanılamaz. **/database**<br /><br /> Dosya adını bağlantı dizesine eklemeyin. Bunun yerine, dosya adını giriş dosyası olarak komut satırına ekleyin. Örneğin, aşağıdaki satırda "c:\northwnd.mdf" giriş dosyası olarak belirtilir: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.|  
|**/timetime:** * \<saniye>*|SqlMetal veritabanına eriştiğinde, zaman aşımı değerini belirtir. Varsayılan değer: 0 (yani, zaman sınırı yok).|  
  
 **Çıkarma seçenekleri**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/görünümler**|Veritabanı görünümlerini ayıklar.|  
|**/fonksiyonlar**|Veritabanı işlevlerini ayıklar.|  
|**/sprocs**|Saklı yordamları ayıklar.|  
  
 **Çıkış seçenekleri**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/dbml** *[:dosya]*|Çıkışı .dbml olarak gönderir. **/harita** seçeneği ile kullanılamaz.|  
|**/kod** *[:dosya]*|Çıkışı kaynak kodu olarak gönderir. **/dbml** seçeneği ile kullanılamaz.|  
|**/harita** *[:dosya]*|Öznitelikler yerine bir XML eşleme dosyası oluşturur. **/dbml** seçeneği ile kullanılamaz.|  
  
 **Çeşitli**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/language:** * \<dil>*|Kaynak kod dilini belirtir.<br /><br /> Geçerli * \<dil>*: vb, csharp.<br /><br /> Varsayılan değer: Kod dosyası adındaki uzantıdan türetilir.|  
|**/namespace:** * \<isim>*|Üretilen kodun ad alanını belirtir. Varsayılan değer: ad alanı yok.|  
|**/context:** * \<tip>*|Veri bağlamı sınıfının adını belirtir. Varsayılan değer: Veritabanı adından türetilir.|  
|**/entitybase:** * \<tip>*|Üretilen kodda varlık sınıflarının temel sınıfını belirtir. Varsayılan değer: Varlıkların temel sınıfı yoktur.|  
|**/çoğulize**|Sınıf ve üye adlarını otomatik olarak çoğullaştırır veya tekilleştirir.<br /><br /> Bu seçenek yalnızca ABD İngilizcesi sürümünde kullanılabilir.|  
|**/serialization:** * \<seçenek>*|Seri hale getirilebilir sınıflar oluşturur.<br /><br /> Geçerli * \<seçenek>*: Yok, Tek yönlü. Varsayılan değer: Hiçbiri.<br /><br /> Daha fazla bilgi için [Serileştirme'ye](../data/adonet/sql/linq/serialization.md)bakın.|  
  
 **Giriş Dosyası**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**\<giriş dosyası>**|SQL Server Express .mdf dosyası, SQL Server Compact 3.5 .sdf dosyası veya .dbml ara dosya belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 SqlMetal işlevi aslında iki adımdan oluşur:  
  
- Veritabanını meta verilerini bir .dbml dosyasına ayıklama.  
  
- Kod çıktı dosyası oluşturma.  
  
     Uygun komut satırı seçeneklerini kullanarak Visual Basic veya C# kaynak kodu üretebilir veya bir XML eşleme dosyası oluşturabilirsiniz.  
  
 Meta verileri bir .mdf dosyasından ayıklamak için, .mdf dosyası adını tüm diğer seçeneklerden sonra belirtmeniz gerekir.  
  
 **/sunucu belirtilmemişse,** **localhost/sqlexpress** varsayılr.  
  
 Microsoft SQL Server 2005, aşağıdaki koşullardan biri veya birkaçı doğruysa bir özel durum oluşturur:  
  
- SqlMetal, kendi kendini çağıran bir saklı yordam ayıklamaya çalışır.  
  
- Bir saklı yordam, işlev veya görünümün iç içe geçme düzeyini 32'yi aşıyor.  
  
     SqlMetal, bu özel durumu yakalar ve bir uyarı olarak bildirir.  
  
 Bir giriş dosyası adı belirtmek için, adı komut satırına giriş dosyası olarak ekleyin. Bağlantı dizesindeki dosya adının eklenmesi **(/conn** seçeneğini kullanarak) desteklenmez.  
  
## <a name="examples"></a>Örnekler  
 Ayıklanan SQL meta verileri içeren bir .dbml dosyası oluşturun:  
  
 **sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**  
  
 SQL Server Express kullanarak bir .mdf dosyasından ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:  
  
 **sqlmetal /dbml:mymeta.dbml mydbfile.mdf**  
  
 SQL Server Express'ten ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:  
  
 **sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**  
  
 Dbml meta veri dosyasından kaynak kodu oluşturun:  
  
 **sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**  
  
 Doğrudan SQL meta verilerinden kaynak kodu oluşturun:  
  
 **sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**  
  
> [!NOTE]
> Northwind örnek veritabanıile **/çoğulize** seçeneğini kullandığınızda, aşağıdaki davranışa dikkat edin. SqlMetal tablolar için satır türünde adlar oluşturduğunda, tablo adları tekildir. Tablolar için <xref:System.Data.Linq.DataContext> özellikler yaptığında, tablo adları çoğul olur. Tesadüfen, Northwind örnek veritabanındaki tablolar zaten çoğuldur. Bu nedenle, bu bölümün çalıştığını görmezsiniz. Veritabanı tablolarını tekil olarak adlandırmak ortak uygulama olsa da, toplulukları çoğul olarak adlandırmak da .NET'te ortak bir uygulamadır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Visual Basic veya C# içinde Nesne Modeli Oluşturma](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [LINQ to SQL’de Kod Oluşturma](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Dış Eşleme](../data/adonet/sql/linq/external-mapping.md)
