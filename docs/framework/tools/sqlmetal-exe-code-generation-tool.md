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
ms.openlocfilehash: 94ed6328857f6e77cea150d69719322d3aaaea69
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44338317"
---
# <a name="sqlmetalexe-code-generation-tool"></a>SqlMetal.exe (Kod Üretme Aracı)
SqlMetal komut satırı aracı için kod ve eşleme üretir [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] bileşeninin [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Bu konunun ilerisinde görünen seçenekleri uygulayarak, SqlMetal'den aşağıdakileri içeren çeşitli farklı eylemler gerçekleştirmesini isteyebilirsiniz:  
  
-   Bir veritabanından, kaynak kodu ve eşleme öznitelikleri veya bir eşleme dosyası oluşturmak.  
  
-   Bir veritabanından, dosya özelleştirme için bir ara veritabanı işaretleme dili (.dbml) dosyası oluşturmak.  
  
-   Bir .dbml dosyasından, kod veya eşleme öznitelikleri veya bir eşleme dosyası üretmek.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Varsayılan olarak, dosya şu konumdadır `drive`: \Program SDKs\Windows\v`n.nn`\bin. Visual Studio yüklemezseniz da SQLMetal dosyasını indirerek edinebilirsiniz [Windows SDK'sı](https://go.microsoft.com/fwlink/?LinkId=142225).  
  
> [!NOTE]
>  Visual Studio kullanan geliştiriciler de kullanabilir [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] varlık sınıfları üretmek için. Komut satırı yaklaşımı, büyük veritabanları için uygun düşmektedir. SqlMetal bir komut satırı aracı olduğundan, bir oluşturma işleminde kullanabilirsiniz.  
  
 Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md). Komut isteminde aşağıdaki komutu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a>Seçenekler  
 En yeni seçenek listesini görüntülemek için şunu yazın `sqlmetal /?` konumda bir komut isteminde.  
  
 **Bağlantı seçenekleri**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ Server:**  *\<adı >*|Veritabanı sunucusu adını belirtir.|  
|**/ Veritabanı:**  *\<adı >*|Sunucuda veritabanı kataloğu belirtir.|  
|**/ User:**  *\<adı >*|Oturum açma kullanıcı kimliği belirtir. Varsayılan değer: Windows kimlik doğrulaması kullan.|  
|**/ Password:**  *\<parolası >*|Oturum açma parolasını belirtir. Varsayılan değer: Windows kimlik doğrulaması kullan.|  
|**/ conn:**  *\<bağlantı dizesi >*|Veritabanı bağlantısı dizesi belirtir. İle birlikte kullanılamaz **/Server**, **/veritabanı**, **/user**, veya **/Password** seçenekleri.<br /><br /> Dosya adını bağlantı dizesine eklemeyin. Bunun yerine, dosya adını giriş dosyası olarak komut satırına ekleyin. Örneğin, aşağıdaki satır giriş dosyası olarak "c:\northwnd.mdf"yi"belirtir: **sqlmetal /code:"c:\northwind.cs "/language:csharp"c:\northwnd.mdf"yi"**.|  
|**/ timeout:**  *\<saniye >*|SqlMetal veritabanına eriştiğinde, zaman aşımı değerini belirtir. Varsayılan değer: 0 (yani, zaman sınırı yok).|  
  
 **Ayıklama seçenekleri**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Views**|Veritabanı görünümlerini ayıklar.|  
|**/Functions**|Veritabanı işlevlerini ayıklar.|  
|**/sprocs**|Saklı yordamları ayıklar.|  
  
 **Çıkış Seçenekleri**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/DBML** *[: dosyası]*|Çıkışı .dbml olarak gönderir. İle birlikte kullanılamaz **/map** seçeneği.|  
|**/ code** *[: dosyası]*|Çıkışı kaynak kodu olarak gönderir. İle birlikte kullanılamaz **/dbml** seçeneği.|  
|**/ map** *[: dosyası]*|Öznitelikler yerine bir XML eşleme dosyası oluşturur. İle birlikte kullanılamaz **/dbml** seçeneği.|  
  
 **Çeşitli**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Language:**  *\<dil >*|Kaynak kod dilini belirtir.<br /><br /> Geçerli  *\<dil >*: vb, csharp.<br /><br /> Varsayılan değer: Kod dosyası adındaki uzantıdan türetilir.|  
|**/ Namespace:**  *\<adı >*|Üretilen kodun ad alanını belirtir. Varsayılan değer: ad alanı yok.|  
|**/ Context:**  *\<türü >*|Veri bağlamı sınıfının adını belirtir. Varsayılan değer: Veritabanı adından türetilir.|  
|**/entitybase:**  *\<türü >*|Üretilen kodda varlık sınıflarının temel sınıfını belirtir. Varsayılan değer: Varlıkların temel sınıfı yoktur.|  
|**/ pluralize**|Sınıf ve üye adlarını otomatik olarak çoğullaştırır veya tekilleştirir.<br /><br /> Bu seçenek yalnızca ABD bölgesinde kullanılabilir İngilizce sürümü.|  
|**/Serialization:**  *\<seçeneği >*|Seri hale getirilebilir sınıflar oluşturur.<br /><br /> Geçerli  *\<seçeneği >*: hiçbiri, tek yönlü. Varsayılan değer: Hiçbiri.<br /><br /> Daha fazla bilgi için [serileştirme](../../../docs/framework/data/adonet/sql/linq/serialization.md).|  
  
 **Giriş dosyası**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**\<Giriş dosyası >**|Bir SQL Server Express .mdf dosyası belirtir bir [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf dosyası veya bir .dbml Ara dosyası.|  
  
## <a name="remarks"></a>Açıklamalar  
 SqlMetal işlevi aslında iki adımdan oluşur:  
  
-   Veritabanını meta verilerini bir .dbml dosyasına ayıklama.  
  
-   Kod çıktı dosyası oluşturma.  
  
     Uygun komut satırı seçeneklerini kullanarak, Visual Basic veya C# kaynak kodu oluşturabilir veya bir XML eşleme dosyası üretebilirsiniz.  
  
 Meta verileri bir .mdf dosyasından ayıklamak için, .mdf dosyası adını tüm diğer seçeneklerden sonra belirtmeniz gerekir.  
  
 Hayır ise **/Server** belirtilen **localhost/sqlexpress** varsayılır.  
  
 [!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)] bir veya daha fazla aşağıdaki koşullardan biri doğruysa, bir özel durum oluşturur:  
  
-   SqlMetal, kendi kendini çağıran bir saklı yordam ayıklamaya çalışır.  
  
-   Bir saklı yordam, işlev veya görünümün iç içe geçme düzeyini 32'yi aşıyor.  
  
     SqlMetal, bu özel durumu yakalar ve bir uyarı olarak bildirir.  
  
 Bir giriş dosyası adı belirtmek için, adı komut satırına giriş dosyası olarak ekleyin. Dosya adının bağlantı dizesine eklenmesi (kullanarak **/conn** seçeneği) desteklenmiyor.  
  
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
>  Kullanırken **/ pluralize** seçeneğini Northwind örnek veritabanıyla birlikte, aşağıdaki davranışa dikkat edin. SqlMetal tablolar için satır türünde adlar oluşturduğunda, tablo adları tekildir. Ne zaman kolaylaştırır <xref:System.Data.Linq.DataContext> özellikleri tablolar için tablo adları çoğuldur. Tesadüfen, Northwind örnek veritabanındaki tablolar zaten çoğuldur. Bu nedenle, bu bölümün çalıştığını görmezsiniz. Veritabanı tablolarını tekil olarak adlandırmak ortak uygulama olsa da, toplulukları çoğul olarak adlandırmak da .NET'te ortak bir uygulamadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Visual Basic veya C# içinde Nesne Modeli Oluşturma](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 [LINQ to SQL’de Kod Oluşturma](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [Dış Eşleme](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
