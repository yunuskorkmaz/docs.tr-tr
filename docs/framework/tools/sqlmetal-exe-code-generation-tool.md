---
title: "SqlMetal.exe (Kod Üretme Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c54f304117c86066e18bfb40f3b3640819647ac0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="sqlmetalexe-code-generation-tool"></a>SqlMetal.exe (Kod Üretme Aracı)
Kod ve eşleme için SqlMetal komut satırı aracı oluşturur [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] bileşenini [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Bu konunun ilerisinde görünen seçenekleri uygulayarak, SqlMetal'den aşağıdakileri içeren çeşitli farklı eylemler gerçekleştirmesini isteyebilirsiniz:  
  
-   Bir veritabanından, kaynak kodu ve eşleme öznitelikleri veya bir eşleme dosyası oluşturmak.  
  
-   Bir veritabanından, dosya özelleştirme için bir ara veritabanı işaretleme dili (.dbml) dosyası oluşturmak.  
  
-   Bir .dbml dosyasından, kod veya eşleme öznitelikleri veya bir eşleme dosyası üretmek.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Varsayılan olarak, dosyası şu konumdadır `drive`: \Program SDKs\Windows\v`n.nn`\bin. Visual Studio yüklemezseniz, ayrıca SQLMetal dosya yükleyerek alabilirsiniz [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225).  
  
> [!NOTE]
>  Visual Studio kullanan geliştiriciler de kullanabilir [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] sınıflar oluşturmak için. Komut satırı yaklaşımı, büyük veritabanları için uygun düşmektedir. SqlMetal bir komut satırı aracı olduğundan, bir oluşturma işleminde kullanabilirsiniz.  
  
 Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md). Komut isteminde aşağıdakileri yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a>Seçenekler  
 En son geçerli seçenek listesini görüntülemek için şunu yazın `sqlmetal /?` yüklü konumdan bir komut isteminde.  
  
 **Bağlantı seçenekleri**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ Server:**  *\<adı >*|Veritabanı sunucusu adını belirtir.|  
|**/ Veritabanı:**  *\<adı >*|Sunucuda veritabanı kataloğu belirtir.|  
|**/ User:**  *\<adı >*|Oturum açma kullanıcı kimliği belirtir. Varsayılan değer: Windows kimlik doğrulaması kullan.|  
|**/ Password:**  *\<parolası >*|Oturum açma parolasını belirtir. Varsayılan değer: Windows kimlik doğrulaması kullan.|  
|**/ conn:**  *\<bağlantı dizesi >*|Veritabanı bağlantısı dizesi belirtir. Kullanılamaz **/Server**, **/veritabanı**, **/user**, veya **/Password** seçenekleri.<br /><br /> Dosya adını bağlantı dizesine eklemeyin. Bunun yerine, dosya adını giriş dosyası olarak komut satırına ekleyin. Örneğin, aşağıdaki satırı "c:\northwnd.mdf" Giriş dosyası belirtir: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.|  
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
|**/DBML** *[: dosyası]*|Çıkışı .dbml olarak gönderir. Kullanılamaz **/map** seçeneği.|  
|**/ kod** *[: dosyası]*|Çıkışı kaynak kodu olarak gönderir. Kullanılamaz **/dbml** seçeneği.|  
|**/ map** *[: dosyası]*|Öznitelikler yerine bir XML eşleme dosyası oluşturur. Kullanılamaz **/dbml** seçeneği.|  
  
 **Çeşitli**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Language:**  *\<dil >*|Kaynak kod dilini belirtir.<br /><br /> Geçerli  *\<dil >*: vb, csharp.<br /><br /> Varsayılan değer: Kod dosyası adındaki uzantıdan türetilir.|  
|**/ Namespace:**  *\<adı >*|Üretilen kodun ad alanını belirtir. Varsayılan değer: ad alanı yok.|  
|**/ Context:**  *\<türü >*|Veri bağlamı sınıfının adını belirtir. Varsayılan değer: Veritabanı adından türetilir.|  
|**/entitybase:**  *\<türü >*|Üretilen kodda varlık sınıflarının temel sınıfını belirtir. Varsayılan değer: Varlıkların temel sınıfı yoktur.|  
|**/ Çoğul**|Sınıf ve üye adlarını otomatik olarak çoğullaştırır veya tekilleştirir.<br /><br /> Bu seçenek yalnızca ABD'de kullanılabilir. İngilizce sürümü.|  
|**/Serialization:**  *\<seçeneği >*|Seri hale getirilebilir sınıflar oluşturur.<br /><br /> Geçerli  *\<seçeneği >*: None, Unidirectional. Varsayılan değer: Hiçbiri.<br /><br /> Daha fazla bilgi için bkz: [seri hale getirme](../../../docs/framework/data/adonet/sql/linq/serialization.md).|  
  
 **Giriş dosyası**  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**\<Giriş dosyası >**|Bir SQL Server Express .mdf dosyasını belirten bir [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf dosya ya da .dbml Ara dosyası.|  
  
## <a name="remarks"></a>Açıklamalar  
 SqlMetal işlevi aslında iki adımdan oluşur:  
  
-   Veritabanını meta verilerini bir .dbml dosyasına ayıklama.  
  
-   Kod çıktı dosyası oluşturma.  
  
     Komut satırı seçeneklerini kullanarak, üretebilir [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] veya C# kaynak kodu veya bir XML eşleme dosyası oluşturabilirsiniz.  
  
 Meta verileri bir .mdf dosyasından ayıklamak için, .mdf dosyası adını tüm diğer seçeneklerden sonra belirtmeniz gerekir.  
  
 Öyle değilse **/Server** belirtilirse, **localhost/sqlexpress** varsayılır.  
  
 [!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)]bir veya daha fazla aşağıdaki koşullar doğruysa, bir özel durum oluşturur:  
  
-   SqlMetal, kendi kendini çağıran bir saklı yordam ayıklamaya çalışır.  
  
-   Bir saklı yordam, işlev veya görünümün iç içe geçme düzeyini 32'yi aşıyor.  
  
     SqlMetal, bu özel durumu yakalar ve bir uyarı olarak bildirir.  
  
 Bir giriş dosyası adı belirtmek için, adı komut satırına giriş dosyası olarak ekleyin. Dosya adı bağlantı dizesinde dahil olmak üzere (kullanarak **/conn** seçeneği) desteklenmiyor.  
  
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
>  Kullandığınızda **/ çoğul** seçeneği Northwind örnek veritabanı ile aşağıdaki davranışa dikkat edin. SqlMetal tablolar için satır türünde adlar oluşturduğunda, tablo adları tekildir. Ne zaman kolaylaştırır <xref:System.Data.Linq.DataContext> özellikleri tablolar için tablo adlarının çoğul. Tesadüfen, Northwind örnek veritabanındaki tablolar zaten çoğuldur. Bu nedenle, bu bölümün çalıştığını görmezsiniz. Veritabanı tablolarını tekil olarak adlandırmak ortak uygulama olsa da, toplulukları çoğul olarak adlandırmak da .NET'te ortak bir uygulamadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Visual Basic veya C# içinde nesne modeli oluşturma](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 [LINQ-SQL kod oluşturma](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [Dış eşleme](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
