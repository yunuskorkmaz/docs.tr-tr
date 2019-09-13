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
ms.openlocfilehash: 0d12196acab5a50f7dd6fc78e6dccc098cf3e2de
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894614"
---
# <a name="sqlmetalexe-code-generation-tool"></a>SqlMetal.exe (Kod Üretme Aracı)
SqlMetal komut satırı aracı .NET Framework [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] bileşeni için kod ve eşleme oluşturur. Bu konunun ilerisinde görünen seçenekleri uygulayarak, SqlMetal'den aşağıdakileri içeren çeşitli farklı eylemler gerçekleştirmesini isteyebilirsiniz:  
  
- Bir veritabanından, kaynak kodu ve eşleme öznitelikleri veya bir eşleme dosyası oluşturmak.  
  
- Bir veritabanından, dosya özelleştirme için bir ara veritabanı işaretleme dili (.dbml) dosyası oluşturmak.  
  
- Bir .dbml dosyasından, kod veya eşleme öznitelikleri veya bir eşleme dosyası üretmek.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Varsayılan olarak, dosya şu konumda `drive`bulunur: \Program Files\Microsoft sdks\windows\v \Bin.`n.nn` Visual Studio 'Yu yüklemezseniz, [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225)Indirerek SqlMetal dosyasını da alabilirsiniz.  
  
> [!NOTE]
> Visual Studio kullanan geliştiriciler de Nesne İlişkisel Tasarımcısı varlık sınıfları oluşturmak için kullanabilir. Komut satırı yaklaşımı, büyük veritabanları için uygun düşmektedir. SqlMetal bir komut satırı aracı olduğundan, bir oluşturma işleminde kullanabilirsiniz.  
  
 Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md). Komut isteminde aşağıdakileri yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a>Seçenekler  
 En güncel seçenek listesini görüntülemek için, yüklü konumdan `sqlmetal /?` bir komut istemine yazın.  
  
 **Bağlantı seçenekleri**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Server:**  *ad\<>*|Veritabanı sunucusu adını belirtir.|  
|**/Database:**  *ad\<>*|Sunucuda veritabanı kataloğu belirtir.|  
|**/User:**  *ad\<>*|Oturum açma kullanıcı kimliği belirtir. Varsayılan değer: Windows kimlik doğrulamasını kullanın.|  
|**/Password:**  *parola\<>*|Oturum açma parolasını belirtir. Varsayılan değer: Windows kimlik doğrulamasını kullanın.|  
|**/Conn:**  *bağlantıdizesi\<>*|Veritabanı bağlantısı dizesi belirtir. **/Server**, **/Database**, **/User**veya **/Password** seçenekleriyle birlikte kullanılamaz.<br /><br /> Dosya adını bağlantı dizesine eklemeyin. Bunun yerine, dosya adını giriş dosyası olarak komut satırına ekleyin. Örneğin, aşağıdaki satır giriş dosyası olarak "c:\kuzeydoğu WND.mdf" belirtir: **SqlMetal/Code: "c:\Northwind.cs"/Language: CSharp "c:\kuzeydoğu WND.mdf"** .|  
|**/Timeout:**  *saniyeler\<>*|SqlMetal veritabanına eriştiğinde, zaman aşımı değerini belirtir. Varsayılan değer: 0 (yani, zaman sınırı yoktur).|  
  
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
|**/Code** *[: dosya]*|Çıkışı kaynak kodu olarak gönderir. **/DBML** seçeneğiyle birlikte kullanılamaz.|  
|**/Map** *[: dosya]*|Öznitelikler yerine bir XML eşleme dosyası oluşturur. **/DBML** seçeneğiyle birlikte kullanılamaz.|  
  
 **Çeşitli**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Language:**  *dil\<>*|Kaynak kod dilini belirtir.<br /><br /> *Geçerli\<dil >* : vb, CSharp.<br /><br /> Varsayılan değer: Kod dosyası adındaki uzantıdan türetilir.|  
|**/Namespace:**  *ad\<>*|Üretilen kodun ad alanını belirtir. Varsayılan değer: ad alanı yok.|  
|**/Context:**  *tür\<>*|Veri bağlamı sınıfının adını belirtir. Varsayılan değer: Veritabanı adından türetilir.|  
|**/entitybase:**  *tür\<>*|Üretilen kodda varlık sınıflarının temel sınıfını belirtir. Varsayılan değer: Varlıkların temel sınıfı yok.|  
|**/plurleştir**|Sınıf ve üye adlarını otomatik olarak çoğullaştırır veya tekilleştirir.<br /><br /> Bu seçenek yalnızca ABD 'de kullanılabilir İngilizce sürümü.|  
|**/Serialization:**  *seçenek\<>*|Seri hale getirilebilir sınıflar oluşturur.<br /><br /> *Geçerli\<Seçenek >* : Hiçbiri, tek yönlü. Varsayılan değer: Yok.<br /><br /> Daha fazla bilgi için bkz. [serileştirme](../../../docs/framework/data/adonet/sql/linq/serialization.md).|  
  
 **Giriş dosyası**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**\<giriş dosyası >**|Bir SQL Server Express. mdf dosyası, bir SQL Server Compact 3,5. sdf dosyası veya. dbml ara dosyası belirtir.|  
  
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
  
 **sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**  
  
 Dbml meta veri dosyasından kaynak kodu oluşturun:  
  
 **SqlMetal/Namespace: Nwind/Code: nrüzgar. cs/Language: CSharp mymetal. dbml**  
  
 Doğrudan SQL meta verilerinden kaynak kodu oluşturun:  
  
 **SqlMetal/Server: sunucum/veritabanı: Northwind/Namespace: Nwind/Code: nrüzgar. cs/Language: CSharp**  
  
> [!NOTE]
> Northwind örnek veritabanıyla **/plurleştir** seçeneğini kullandığınızda aşağıdaki davranışa göz önünde bulabilirsiniz. SqlMetal tablolar için satır türünde adlar oluşturduğunda, tablo adları tekildir. Tablolar için Özellikler <xref:System.Data.Linq.DataContext> yaptığında tablo adları plural olur. Tesadüfen, Northwind örnek veritabanındaki tablolar zaten çoğuldur. Bu nedenle, bu bölümün çalıştığını görmezsiniz. Veritabanı tablolarını tekil olarak adlandırmak ortak uygulama olsa da, toplulukları çoğul olarak adlandırmak da .NET'te ortak bir uygulamadır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Visual Basic veya içinde nesne modeli oluşturmaC#](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [LINQ to SQL’de Kod Oluşturma](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Dış Eşleme](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
