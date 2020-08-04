---
title: SqlMetal.exe (Kod Üretme Aracı)
description: Kod oluşturma aracını SqlMetal.exe anlayın. .NET ' in LINQ to SQL bileşeni için kod ve eşleme oluşturmak için aracını kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: 84cad85a7a9fc4b420b57543b7f258607be4ab52
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517054"
---
# <a name="sqlmetalexe-code-generation-tool"></a>SqlMetal.exe (Kod Üretme Aracı)
SqlMetal komut satırı aracı .NET Framework bileşeni için kod ve eşleme oluşturur [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] . Bu konunun ilerisinde görünen seçenekleri uygulayarak, SqlMetal'den aşağıdakileri içeren çeşitli farklı eylemler gerçekleştirmesini isteyebilirsiniz:  
  
- Bir veritabanından, kaynak kodu ve eşleme öznitelikleri veya bir eşleme dosyası oluşturmak.  
  
- Bir veritabanından, dosya özelleştirme için bir ara veritabanı işaretleme dili (.dbml) dosyası oluşturmak.  
  
- Bir .dbml dosyasından, kod veya eşleme öznitelikleri veya bir eşleme dosyası üretmek.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Varsayılan olarak, dosya şu konumda bulunur `drive` : \Program Files\Microsoft SDKs\Windows\v `n.nn` \Bin. Visual Studio 'Yu yüklemezseniz, [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225)Indirerek SqlMetal dosyasını da alabilirsiniz.  
  
> [!NOTE]
> Visual Studio kullanan geliştiriciler de Nesne İlişkisel Tasarımcısı varlık sınıfları oluşturmak için kullanabilir. Komut satırı yaklaşımı, büyük veritabanları için uygun düşmektedir. SqlMetal bir komut satırı aracı olduğundan, bir oluşturma işleminde kullanabilirsiniz.  
  
 Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md). Komut isteminde aşağıdakileri yazın:  
  
## <a name="syntax"></a>Syntax  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a>Seçenekler  
 En güncel seçenek listesini görüntülemek için, `sqlmetal /?` yüklü konumdan bir komut istemine yazın.  
  
 **Bağlantı seçenekleri**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Server:***\<name>*|Veritabanı sunucusu adını belirtir.|  
|**/Database:***\<name>*|Sunucuda veritabanı kataloğu belirtir.|  
|**/User:***\<name>*|Oturum açma kullanıcı kimliğini belirtir. Varsayılan değer: Windows kimlik doğrulamasını kullanın.|  
|**/Password:***\<password>*|Oturum açma parolasını belirtir. Varsayılan değer: Windows kimlik doğrulaması kullan.|  
|**/Conn:***\<connection string>*|Veritabanı bağlantısı dizesi belirtir. **/Server**, **/Database**, **/User**veya **/Password** seçenekleriyle birlikte kullanılamaz.<br /><br /> Dosya adını bağlantı dizesine eklemeyin. Bunun yerine, dosya adını giriş dosyası olarak komut satırına ekleyin. Örneğin, aşağıdaki satır giriş dosyası olarak "c:\kuzeydoğu WND.mdf" belirtir: **SqlMetal/Code: "c:\Northwind.cs"/Language: CSharp "c:\kuzeydoğu WND.mdf"**.|  
|**/Timeout:***\<seconds>*|SqlMetal veritabanına eriştiğinde, zaman aşımı değerini belirtir. Varsayılan değer: 0 (yani, zaman sınırı yok).|  
  
 **Ayıklama seçenekleri**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/views**|Veritabanı görünümlerini ayıklar.|  
|**/Functions**|Veritabanı işlevlerini ayıklar.|  
|**/sprocs**|Saklı yordamları ayıklar.|  
  
 **Çıkış seçenekleri**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/DBML** *[: dosya]*|Çıkışı .dbml olarak gönderir. **/Map** seçeneğiyle birlikte kullanılamaz.|  
|**/Code** *[: File]*|Çıkışı kaynak kodu olarak gönderir. **/DBML** seçeneğiyle birlikte kullanılamaz.|  
|**/Map** *[: dosya]*|Öznitelikler yerine bir XML eşleme dosyası oluşturur. **/DBML** seçeneğiyle birlikte kullanılamaz.|  
  
 **Çeşitli**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Language:***\<language>*|Kaynak kod dilini belirtir.<br /><br /> Geçerli *\<language>* : vb, CSharp.<br /><br /> Varsayılan değer: Kod dosyası adındaki uzantıdan türetilir.|  
|**/Namespace:***\<name>*|Üretilen kodun ad alanını belirtir. Varsayılan değer: ad alanı yok.|  
|**/Context:***\<type>*|Veri bağlamı sınıfının adını belirtir. Varsayılan değer: Veritabanı adından türetilir.|  
|**/entitybase:***\<type>*|Üretilen kodda varlık sınıflarının temel sınıfını belirtir. Varsayılan değer: Varlıkların temel sınıfı yoktur.|  
|**/plurleştir**|Sınıf ve üye adlarını otomatik olarak çoğullaştırır veya tekilleştirir.<br /><br /> Bu seçenek yalnızca ABD İngilizcesi sürümünde kullanılabilir.|  
|**/Serialization:***\<option>*|Seri hale getirilebilir sınıflar oluşturur.<br /><br /> Geçerli *\<option>* : None, tek yönlü. Varsayılan değer: Hiçbiri.<br /><br /> Daha fazla bilgi için bkz. [serileştirme](../data/adonet/sql/linq/serialization.md).|  
  
 **Giriş Dosyası**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**\<input file>**|Bir SQL Server Express. mdf dosyası, bir SQL Server Compact 3,5. sdf dosyası veya. dbml ara dosyası belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 SqlMetal işlevi aslında iki adımdan oluşur:  
  
- Veritabanını meta verilerini bir .dbml dosyasına ayıklama.  
  
- Kod çıktı dosyası oluşturma.  
  
     Uygun komut satırı seçeneklerini kullanarak Visual Basic veya C# kaynak kodu oluşturabilir veya bir XML eşleme dosyası üretebilirsiniz.  
  
 Meta verileri bir .mdf dosyasından ayıklamak için, .mdf dosyası adını tüm diğer seçeneklerden sonra belirtmeniz gerekir.  
  
 **/Server** belirtilmemişse, **localhost/sqlexpress** varsayılır.  
  
 Microsoft SQL Server 2005 aşağıdaki koşullardan biri veya daha fazlası doğru ise bir özel durum oluşturur:  
  
- SqlMetal, kendi kendini çağıran bir saklı yordam ayıklamaya çalışır.  
  
- Bir saklı yordam, işlev veya görünümün iç içe geçme düzeyini 32'yi aşıyor.  
  
     SqlMetal, bu özel durumu yakalar ve bir uyarı olarak bildirir.  
  
 Bir giriş dosyası adı belirtmek için, adı komut satırına giriş dosyası olarak ekleyin. Dosya adının bağlantı dizesine dahil edilmesi ( **/Conn** seçeneği kullanılarak) desteklenmez.  
  
## <a name="examples"></a>Örnekler  
 Ayıklanan SQL meta verileri içeren bir .dbml dosyası oluşturun:  
  
 **SqlMetal/Server: sunucum/veritabanı: Northwind/DBML: mymeta. dbml**  
  
 SQL Server Express kullanarak bir .mdf dosyasından ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:  
  
 **SqlMetal/DBML: mymeta. dbml mydbfile. mdf**  
  
 SQL Server Express'ten ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:  
  
 **SqlMetal/Server: .\SQLEXPRESS/DBML: mymeta. dbml/Database: Northwind**  
  
 Dbml meta veri dosyasından kaynak kodu oluşturun:  
  
 **SqlMetal/Namespace: Nwind/Code: nrüzgar. cs/Language: CSharp mymetal. dbml**  
  
 Doğrudan SQL meta verilerinden kaynak kodu oluşturun:  
  
 **SqlMetal/Server: sunucum/veritabanı: Northwind/Namespace: Nwind/Code: nrüzgar. cs/Language: CSharp**  
  
> [!NOTE]
> Northwind örnek veritabanıyla **/plurleştir** seçeneğini kullandığınızda aşağıdaki davranışa göz önünde bulabilirsiniz. SqlMetal tablolar için satır türünde adlar oluşturduğunda, tablo adları tekildir. <xref:System.Data.Linq.DataContext>Tablolar için özellikler yaptığında tablo adları plural olur. Tesadüfen, Northwind örnek veritabanındaki tablolar zaten çoğuldur. Bu nedenle, bu bölümün çalıştığını görmezsiniz. Veritabanı tablolarını tekil olarak adlandırmak ortak uygulama olsa da, toplulukları çoğul olarak adlandırmak da .NET'te ortak bir uygulamadır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Visual Basic veya C# içinde Nesne Modeli Oluşturma](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [LINQ to SQL’de Kod Oluşturma](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Dış Eşleme](../data/adonet/sql/linq/external-mapping.md)
