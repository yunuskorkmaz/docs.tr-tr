---
title: "Oracle şema koleksiyonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2ac06c78670b4113ab718c06423c04c0ea27c208
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="oracle-schema-collections"></a>Oracle şema koleksiyonları
Oracle için Microsoft .NET Framework veri sağlayıcısı ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:  
  
-   Sütunlar  
  
-   Dizinler  
  
-   IndexColumns  
  
-   Yordamlar  
  
-   Diziler  
  
-   Eş anlamlıları  
  
-   tabloları  
  
-   Kullanıcılar  
  
-   Görünümler  
  
-   İşlevler  
  
-   Paketler  
  
-   PackageBodies  
  
-   Arguments  
  
-   UniqueKeys  
  
-   PrimaryKeys  
  
-   ForeignKeys  
  
-   ForeignKeyColumns  
  
-   ProcedureParameters  
  
## <a name="columns"></a>Sütunlar  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Tablo, görünüm veya küme sahibi.|  
|TABLE_NAME|Dize|Tablo, görünüm veya küme adı.|  
|COLUMN_NAME|Dize|Sütun adı.|  
|Kimlik|Ondalık|Sütun sayısı oluşturuldu olarak sıralayın.|  
|VERİ TÜRÜ|Dize|Sütunun veri türü.|  
|UZUNLUĞU|Ondalık|Sütun bayt cinsinden uzunluğu.|  
|DUYARLILIK|Ondalık|Sayı veri türü Ondalık Duyarlığı; ikili duyarlık FLOAT veri türü, için diğer veri türleri null.|  
|ÖLÇEK|Ondalık|Basamak sağında ondalık bir sayı.|  
|BOŞ DEĞER ATANABİLİR|Dize|Bir sütun null değerlere izin verip vermeyeceğini belirtir. Değer N sütunu bir NOT NULL kısıtlaması ise veya sütun birincil anahtarının bir parçası ise.|  
  
## <a name="indexes"></a>Dizinler  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Dizin sahibi|  
|INDEX_NAME|Dize|Dizinin adı.|  
|INDEX_TYPE|Dize|Dizin (NORMAL, bit eşlem, işlevi tabanlı NORMAL, işlevi tabanlı bit eşlem veya etki alanı) türü.|  
|TABLE_OWNER|Dize|Dizinli nesnenin sahibi.|  
|TABLE_NAME|Dize|Dizinli nesnesinin adı.|  
|TABLE_TYPE|Dize|(Örneğin, tablo, küme) dizinli nesnesinin türü.|  
|BENZERSİZLİK|Dize|Dizini benzersiz veya NONUNIQUE olup olmadığı.|  
|SIKIŞTIRMA|Dize|Dizin etkin veya devre dışı olup olmadığı.|  
|PREFIX_LENGTH|Ondalık|Önek sıkıştırma anahtar sütun sayısı.|  
|TABLESPACE_NAME|Dize|Dizini içeren tablo adıdır.|  
|INI_TRANS|Ondalık|İşlem ilk sayısı.|  
|MAX_TRANS|Ondalık|En fazla işlem sayısı.|  
|INITIAL_EXTENT|Ondalık|İlk ölçüde boyutu.|  
|NEXT_EXTENT|Ondalık|İkincil kapsam boyutu.|  
|MIN_EXTENTS|Ondalık|Kapsam segmente izin verilen en düşük sayısı.|  
|MAX_EXTENTS|Ondalık|Kapsam segmente izin verilen maksimum sayısı.|  
|PCT_INCREASE|Ondalık|Kapsam boyutu artış yüzdesi.|  
|PCT_THRESHOLD|Ondalık|Dizin girişi izin verilen blok alanı yüzdesi eşiği.|  
|INCLUDE_COLUMN|Ondalık|Dizini düzenlenmiş tabloda birincil anahtar (taşma dışı) dizine eklenecek sütun kimliği son sütun. Bu sütun için COLUMN_ID sütunun eşlemeleri * _TAB_COLUMNS veri sözlüğü görünümleri.|  
|LİSTE|Ondalık|Bu kesimin ayrılan işlem liste sayısı.|  
|FREELIST_GROUPS|Ondalık|Bu kesimin ayrılan freelist grupları sayısı.|  
|PCT_FREE|Ondalık|Bir blok boş alanı en düşük yüzdesi.|  
|GÜNLÜĞE KAYDETME|Dize|Günlük bilgileri.|  
|BLEVEL|Ondalık|B *-Ağacı düzeyi: kök blok dizinden kendi yaprak bloklarına derinliği. 0 derinliği kök bloğu ve yaprak bloğu aynı olduğunu gösterir.|  
|LEAF_BLOCKS|Ondalık|Dizindeki yaprak bloğu sayısı.|  
|DISTINCT_KEYS|Ondalık|Ayrı dizinli değerlerinin sayısı. BENZERSİZ ve birincil anahtar kısıtlamalarını zorla dizinler için bu değeri (USER_TABLES. tablodaki satır sayısını aynıdır NUM_ROWS).|  
|AVG_LEAF_BLOCKS_PER_KEY|Ondalık|Her farklı değeri dizindeki göründüğü yaprak bloğu en yakın tamsayıya yuvarlanan ortalama sayısı. BENZERSİZ ve birincil anahtar kısıtlamalarını zorla dizinler için bu değer her zaman 1'dir.|  
|AVG_DATA_BLOCKS_PER_KEY|Ondalık|En yakın tamsayıya yuvarlanan dizindeki farklı bir değer gösterdiği tablodaki verileri ortalama sayısı engeller. Bu istatistik dizinli sütunlar için belirli bir değeri içeren satırları içeren veri blokları ortalama sayısıdır.|  
|CLUSTERING_FACTOR|Ondalık|Dizin değerlerine göre tablosundaki satırların sırasını miktarını gösterir.|  
|DURUMU|Dize|Bölümlenmemiş dizini geçerli veya UNUSABLE olup olmadığı.|  
|NUM_ROWS|Ondalık|Dizin içindeki satır sayısını belirtir.|  
|SAMPLE_SIZE|Ondalık|Dizin çözümlemek için kullanılan örnek boyutu.|  
|LAST_ANALYZED|DateTime|Bu dizin analiz edildi en son tarihi.|  
|DERECE|Dize|Dizin tarama için örnek başına iş parçacığı sayısı.|  
|ÖRNEKLERİ|Dize|Hangi örneklerinde sayısı taranacak dizinleri.|  
|BÖLÜMLENMİŞ|Dize|Bu dizin olup bölümlenmiş (Evet &#124; HAYIR).|  
|GEÇİCİ|Dize|Dizin geçici bir tablo üzerinde olup olmadığı.|  
|OLUŞTURULAN|Dize|Dizinin adını sistem olup olmadığını oluşturulan (Y &#124; N).|  
|İKİNCİL|Dize|Dizin Oracle9i veri Kartuş ODCIIndexCreate yöntemi tarafından oluşturulan ikincil bir nesne olup (Y &#124; N).|  
|BUFFER_POOL|Dize|Dizin blokları için kullanılacak varsayılan arabellek havuzunun adı.|  
|USER_STATS|Dize|Olup istatistikleri doğrudan kullanıcı tarafından girilen.|  
|SÜRE|Dize|Geçici bir tablo süresini gösterir: 1) SYS$ oturum: satırları oturum süresi boyunca, 2) SYS$ işlem için korunur: satırları TAMAMLAMA, 3) Null kalıcı tablosu için sonra silinir.|  
|PCT_DIRECT_ACCESS|Ondalık|İkincil bir dizin için dizin düzenlenmiş tablosunda, geçerli satırlarla yüzdesini tahmin|  
|ITYP_OWNER|Dize|Etki alanı dizini için indextype sahibi.|  
|ITYP_NAME|Dize|Etki alanı dizini için indextype adı.|  
|PARAMETRELERİ|Dize|Etki alanı dizini için parametre dizesi.|  
|GLOBAL_STATS|Dize|Bölümlenmiş dizinler için istatistik dizini bir bütün olarak (Evet) çözümleme tarafından toplanan veya İstatistikler temel dizin bölümlerinin ve subpartitions (Hayır) tahmini gösterir.|  
|DOMIDX_STATUS|Dize|Etki alanı dizin durumunu yansıtır. NULL: Belirtilen dizin bir etki alanı dizini değil. : Dizini geçerli bir etki alanı dizin geçerlidir. IDXTYP_INVLD: Bu etki alanı dizininin dizin türü geçersiz.|  
|DOMIDX_OPSTATUS|Dize|Bir etki alanı dizini gerçekleştirilen bir işlem durumunu yansıtır: NULL: Belirtilen dizin bir etki alanı dizini değil. Geçerli: işlem gerçekleştirilirken bir hata olmadan. Başarısız oldu: işlem bir hata ile başarısız oldu.|  
|FUNCIDX_STATUS|Dize|İşlev tabanlı bir dizin durumunu gösterir: NULL: Bu işlevi tabanlı değil dizin, etkin: işlevi tabanlı bir dizin etkin, devre dışı: işlevi tabanlı dizini devre dışı bırakıldı.|  
|JOIN_INDEX|Dize|Bu birleşim dizin olup olmadığını gösterir.|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|INDEX_OWNER|Dize|Dizin sahibi.|  
|INDEX_NAME|Dize|Dizinin adı.|  
|TABLE_OWNER|Dize|Tablo ya da küme sahibi.|  
|TABLE_NAME|Dize|Tablo veya küme adı.|  
|COLUMN_NAME|Dize|Sütun adı veya nesne türü sütunu özniteliği.|  
|COLUMN_POSITION|Ondalık|Sütun veya içinde dizin özniteliği konumu.|  
|COLUMN_LENGTH|Ondalık|Sütun dizini oluşturulmuş uzunluğu.|  
|CHAR_LENGTH|Ondalık|Sütun uzunluğu en fazla codepoint.|  
|DÜZEN|Dize|Olup sütunu azalan sırada sıralanır.|  
  
## <a name="procedures"></a>Yordamlar  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Nesnenin sahibi.|  
|OBJECT_NAME|Dize|Nesnenin adı.|  
|SUBOBJECT_NAME|Dize|Alt nesne (örneğin, bölüm) adı.|  
|OBJECT_ID|Ondalık|Nesne sözlük nesne sayısı.|  
|DATA_OBJECT_ID|Ondalık|Nesne içeren kesim sözlük nesne sayısı.|  
|LAST_DDL_TIME|DateTime|Son değiştirilme (verir ve kaldırılırlar dahil) bir DDL komutundan kaynaklanan nesnesinin için zaman damgası.|  
|ZAMAN DAMGASI|Dize|Zaman damgası (karakter verileri) nesnesinin belirtimi için.|  
|DURUMU|Dize|(Geçerli, geçersiz veya yok) nesnenin durumu.|  
|GEÇİCİ|Dize|Nesne geçici olup (geçerli oturum bu nesnesinde yerleştirilen veri görebilirsiniz).|  
|OLUŞTURULAN|Dize|Bu nesne sistem tarafından oluşturulan adı neydi? (Y &#124; N).|  
|İKİNCİL|Dize|Bu Oracle9i veri Kartuş ODCIIndexCreate yöntemi tarafından oluşturulan ikincil bir nesne olup olmadığını (Y &#124; N).|  
|OLUŞTURULAN|DateTime|Nesnenin oluşturulduğu tarih.|  
  
## <a name="sequences"></a>Diziler  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SEQUENCE_OWNER|Dize|Sıranın sahibinin adı.|  
|SEQUENCE_NAME|Dize|Sıra adı.|  
|MIN_VALUE|Ondalık|En küçük değer dizisi.|  
|MAX_VALUE|Ondalık|En büyük değer dizisi.|  
|INCREMENT_BY|Ondalık|Değer olarak dizisi artırılır.|  
|CYCLE_FLAG|Dize|Sınıra ulaştıktan üzerinde kaydırma geçici dizisi.|  
|ORDER_FLAG|Dize|Sıra numaraları sırayla üretilir.|  
|CACHE_SIZE|Ondalık|Sıra numaraları önbelleğe sayısı.|  
|LAST_NUMBER|Ondalık|Son dizi diske yazılan numarası. Bir dizi önbelleğe alma, yazılan numarası kullanıp kullanmadığını disk dizisi önbelleğe yerleştirilmiş son numarasıdır. Bu sayı, kullanılan son sıra numarasından daha büyük olması olasıdır.|  
  
## <a name="synonyms"></a>Eş anlamlıları  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Eş anlamlı sahibi.|  
|SYNONYM_NAME|Dize|Eş adı.|  
|TABLE_OWNER|Dize|Anlamlının başvuruda nesnenin sahibi.|  
|TABLE_NAME|Dize|Anlamlının başvuruda nesnesinin adı.|  
|DB_LINK|Dize|Varsa, başvurulan veritabanı bağlantısı adı.|  
  
## <a name="tables"></a>tabloları  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Tablonun sahibi.|  
|TABLE_NAME|Dize|Tablonun adı.|  
|TÜRÜ|Dize|Tablo türü.|  
  
## <a name="users"></a>Kullanıcılar  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|NAME|Dize|Kullanıcı adı.|  
|Kimlik|Ondalık|Kullanıcı Kimliği sayısı.|  
|CREATEDATE|DateTime|Kullanıcı oluşturma tarihi.|  
  
## <a name="views"></a>Görünümler  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Görünümün sahibi.|  
|VIEW_NAME|Dize|Görünümün adı.|  
|TEXT_LENGTH|Ondalık|Görünüm metnin uzunluğu.|  
|METİN|Dize|Metni görüntüleyin.|  
|TYPE_TEXT_LENGTH|Ondalık|Belirtilmiş görünüm türü yan tümcesi uzunluğu.|  
|METİN_TÜRÜ|Dize|Yan tümcesi belirtilmiş görünüm türü.|  
|OID_TEXT_LENGTH|Ondalık|İLE OID yan tümcesinde belirtilmiş görünüm uzunluğu.|  
|OID_TEXT|Dize|Türü belirtilmiş görünümü OID yan TÜMCESİYLE.|  
|VIEW_TYPE_OWNER|Dize|Görünümü belirtilmiş görünüm ise görünüm türünü sahibi.|  
|VIEW_TYPE|Dize|Görünümü belirtilmiş görünüm ise Görünüm türü.|  
|SUPERVIEW_NAME|Dize|Değerlendirmesi adı.|  
  
## <a name="functions"></a>İşlevler  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Nesnenin sahibi.|  
|OBJECT_NAME|Dize|Nesnenin adı.|  
|SUBOBJECT_NAME|Dize|Alt nesne (örneğin, bölüm) adı.|  
|OBJECT_ID|Ondalık|Nesne sözlük nesne sayısı.|  
|DATA_OBJECT_ID|Ondalık|Nesne içeren kesim sözlük nesne sayısı.|  
|OBJECT_TYPE|Dize|Nesnenin türü.|  
|OLUŞTURULAN|DateTime|Nesnenin oluşturulduğu tarih.|  
|LAST_DDL_TIME|DateTime|Son değiştirilme (verir ve kaldırılırlar dahil) bir DDL komutundan kaynaklanan nesnesinin için zaman damgası.|  
|ZAMAN DAMGASI|Dize|Nesne (karakter verileri) belirtimi için zaman damgası|  
|DURUMU|Dize|(Geçerli, geçersiz veya yok) nesnenin durumu.|  
|GEÇİCİ|Dize|Nesne geçici olup (geçerli oturum bu nesnesinde yerleştirilen veri görebilirsiniz).|  
|OLUŞTURULAN|Dize|Bu nesne sistem tarafından oluşturulan adı neydi? (Y &#124; N).|  
|İKİNCİL|Dize|Bu Oracle9i veri Kartuş ODCIIndexCreate yöntemi tarafından oluşturulan ikincil bir nesne olup olmadığını (Y &#124; N).|  
  
## <a name="packages"></a>Paketler  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Nesnenin sahibi.|  
|OBJECT_NAME|Dize|Nesnenin adı.|  
|SUBOBJECT_NAME|Dize|Alt nesne (örneğin, bölüm) adı.|  
|OBJECT_ID|Ondalık|Nesne sözlük nesne sayısı.|  
|DATA_OBJECT_ID|Ondalık|Nesne içeren kesim sözlük nesne sayısı.|  
|LAST_DDL_TIME|DateTime|Son değiştirilme (verir ve kaldırılırlar dahil) bir DDL komutundan kaynaklanan nesnesinin için zaman damgası.|  
|ZAMAN DAMGASI|Dize|Zaman damgası (karakter verileri) nesnesinin belirtimi için.|  
|DURUMU|Dize|(Geçerli, geçersiz veya yok) nesnenin durumu.|  
|GEÇİCİ|Dize|Nesne geçici olup (geçerli oturum bu nesnesinde yerleştirilen veri görebilirsiniz).|  
|OLUŞTURULAN|Dize|Bu nesne sistem tarafından oluşturulan adı neydi? (Y &#124; N).|  
|İKİNCİL|Dize|Bu Oracle9i veri Kartuş ODCIIndexCreate yöntemi tarafından oluşturulan ikincil bir nesne olup olmadığını (Y &#124; N).|  
|OLUŞTURULAN|DateTime|Nesnenin oluşturulduğu tarih.|  
  
## <a name="packagebodies"></a>PackageBodies  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Nesnenin sahibi.|  
|OBJECT_NAME|Dize|Nesnenin adı.|  
|SUBOBJECT_NAME|Dize|Alt nesne (örneğin, bölüm) adı.|  
|OBJECT_ID|Ondalık|Nesne sözlük nesne sayısı.|  
|DATA_OBJECT_ID|Ondalık|Nesne içeren kesim sözlük nesne sayısı.|  
|LAST_DDL_TIME|DateTime|Son değiştirilme (verir ve kaldırılırlar dahil) bir DDL komutundan kaynaklanan nesnesinin için zaman damgası.|  
|ZAMAN DAMGASI|Dize|Zaman damgası (karakter verileri) nesnesinin belirtimi için.|  
|DURUMU|Dize|(Geçerli, geçersiz veya yok) nesnenin durumu.|  
|GEÇİCİ|Dize|Nesne geçici olup (geçerli oturum bu nesnesinde yerleştirilen veri görebilirsiniz).|  
|OLUŞTURULAN|Dize|Bu nesne sistem tarafından oluşturulan adı neydi? (Y &#124; N).|  
|İKİNCİL|Dize|Bu Oracle9i veri Kartuş ODCIIndexCreate yöntemi tarafından oluşturulan ikincil bir nesne olup olmadığını (Y &#124; N).|  
|OLUŞTURULAN|DateTime|Nesnenin oluşturulduğu tarih.|  
  
## <a name="arguments"></a>Arguments  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Nesnenin sahibi adı.|  
|PAKET_ADI|Dize|Paket adı.|  
|OBJECT_NAME|Dize|Yordam veya işlev adı.|  
|ARGUMENT_NAME|Dize|Bağımsız değişken adı.|  
|KONUMU|Ondalık|İşlev dönüş değeri için konum bağımsız değişken listesi veya NULL.|  
|SIRASI|Ondalık|Tüm iç içe geçme düzeyi de dahil olmak üzere, bağımsız değişken dizisi.|  
|DEFAULT_VALUE|Dize|Bağımsız değişkeni için varsayılan değer.|  
|DEFAULT_LENGTH|Ondalık|Bağımsız değişkeni için varsayılan değer uzunluğu.|  
|IN_OUT|Dize|Bağımsız değişken yönü (İNÇ, çıkış veya giriş/çıkış).|  
|DATA_LENGTH|Ondalık|Sütun bayt cinsinden uzunluğu.|  
|DATA_PRECISION|Ondalık|Ondalık sayılar (sayı) veya ikili basamak (kayan nokta) cinsinden uzunluğu.|  
|DATA_SCALE|Ondalık|Basamak sağında ondalık bir sayı.|  
|DATA_TYPE|Dize|Bağımsız değişken veri türü.|  
  
## <a name="uniquekeys"></a>UniqueKeys  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Kısıtlama tanımı sahibi.|  
|CONSTRAINT_NAME|Dize|Kısıtlama tanımının adı.|  
|TABLE_NAME|Dize|Kısıtlama tanımıyla tablosu (veya Görünüm) ile ilişkili adı.|  
|SEARCH_CONDITION|Dize|Arama koşulu denetim kısıtlaması için metni.|  
|R_OWNER|Dize|Bir başvuru kısıtlamasında Başvurulan tablonun sahibi.|  
|R_CONSTRAINT_NAME|Dize|Başvurulan tablosu için benzersiz kısıtlamayı tanımı adı.|  
|DELETE_RULE|Dize|Kural için bir başvuru kısıtlamasının (CASCADE veya NO ACTION) silin.|  
|DURUMU|Dize|Zorlama durumu kısıtlaması (etkin veya devre dışı).|  
|DEFERRABLE|Dize|Kısıtlama deferrable olup olmadığı.|  
|DOĞRULANDI|Dize|Olup tüm verileri (veya DOĞRULANMAMIŞ DOĞRULANACAĞINI) kısıtlaması obeys.|  
|OLUŞTURULAN|Dize|Kısıtlamanın adını kullanıcı veya sistem tarafından oluşturulan olup olmadığı.|  
|HATALI|Dize|Bu sınırlama belirsiz bir şekilde bir century belirtir Evet değeri gösterir. Bu belirsizlik kaynaklanan hataları önlemek için ile dört rakamlı yıl TO_DATE işlevi kullanarak kısıtlaması yeniden yazın.|  
|KULLANIR|Dize|Olup etkinleştirilmiş bir kısıtlaması zorlanan zorlanmamış veya.|  
|LAST_CHANGE|DateTime|Ne zaman kısıtlaması en son etkin veya devre dışı|  
|INDEX_OWNER|Dize|Dizin sahibi olan kullanıcı adı|  
|INDEX_NAME|Dize|Dizinin adı|  
  
## <a name="primarykeys"></a>PrimaryKeys  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Kısıtlama tanımı sahibi.|  
|CONSTRAINT_NAME|Dize|Kısıtlama tanımının adı.|  
|TABLE_NAME|Dize|Kısıtlama tanımıyla tablosu (veya Görünüm) ile ilişkili adı.|  
|SEARCH_CONDITION|Dize|Arama koşulu denetim kısıtlaması için metni.|  
|R_OWNER|Dize|Bir başvuru kısıtlamasında Başvurulan tablonun sahibi.|  
|R_CONSTRAINT_NAME|Dize|Başvurulan tablosu için benzersiz kısıtlamayı tanımı adı.|  
|DELETE_RULE|Dize|Kural için bir başvuru kısıtlamasının (CASCADE veya NO ACTION) silin.|  
|DURUMU|Dize|Zorlama durumu kısıtlaması (etkin veya devre dışı).|  
|DEFERRABLE|Dize|Kısıtlama deferrable olup olmadığı.|  
|DOĞRULANDI|Dize|Olup tüm verileri (veya DOĞRULANMAMIŞ DOĞRULANACAĞINI) kısıtlaması obeys.|  
|OLUŞTURULAN|Dize|Kısıtlamanın adını kullanıcı veya sistem tarafından oluşturulan olup olmadığı.|  
|HATALI|Dize|Bu sınırlama belirsiz bir şekilde bir century belirtir Evet değeri gösterir. Bu belirsizlik kaynaklanan hataları önlemek için ile dört rakamlı yıl TO_DATE işlevi kullanarak kısıtlaması yeniden yazın.|  
|KULLANIR|Dize|Olup etkinleştirilmiş bir kısıtlaması zorlanan zorlanmamış veya.|  
|LAST_CHANGE|DateTime|Ne zaman kısıtlaması en son etkin veya devre dışı.|  
|INDEX_OWNER|Dize|Dizin sahibi olan kullanıcı adı.|  
|INDEX_NAME|Dize|Dizinin adı.|  
  
## <a name="foreignkeys"></a>ForeignKeys  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|PRIMARY_KEY_CONSTRAINT_NAME|Dize|Kısıtlama tanımının adı.|  
|PRIMARY_KEY_OWNER|Dize|Kısıtlama tanımı sahibi.|  
|PRIMARY_KEY_TABLE_NAME|Dize|Kısıtlama tanımıyla tablosu (veya Görünüm) ile ilişkili adı|  
|FOREIGN_KEY_OWNER|Dize|Kısıtlama tanımı sahibi.|  
|FOREIGN_KEY_CONSTRIANT_NAME|Dize|Kısıtlama tanımının adı.|  
|FOREIGN_KEY_TABLE_NAME|Dize|Kısıtlama tanımıyla tablosu (veya Görünüm) ile ilişkili adı.|  
|SEARCH_CONDITION|Dize|Arama koşulu denetim kısıtlaması için metin|  
|R_OWNER|Dize|Bir başvuru kısıtlamasında Başvurulan tablonun sahibi.|  
|R_CONSTRAINT_NAME|Dize|Başvurulan tablosu için benzersiz kısıtlamayı tanımı adı.|  
|DELETE_RULE|Dize|Kural için bir başvuru kısıtlamasının (CASCADE veya NO ACTION) silin.|  
|DURUMU|Dize|Zorlama durumu kısıtlaması (etkin veya devre dışı).|  
|DOĞRULANDI|Dize|Olup tüm verileri (veya DOĞRULANMAMIŞ DOĞRULANACAĞINI) kısıtlaması obeys.|  
|OLUŞTURULAN|Dize|Kısıtlamanın adını kullanıcı veya sistem tarafından oluşturulan olup olmadığı.|  
|KULLANIR|Dize|Olup etkinleştirilmiş bir kısıtlaması zorlanan zorlanmamış veya.|  
|LAST_CHANGE|DateTime|Ne zaman kısıtlaması en son etkin veya devre dışı.|  
|INDEX_OWNER|Dize|Dizin sahibi olan kullanıcı adı.|  
|INDEX_NAME|Dize|Dizinin adı.|  
  
## <a name="foreignkeycolumns"></a>ForeignKeyColumns  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Kısıtlama tanımı sahibi.|  
|CONSTRAINT_NAME|Dize|Kısıtlama tanımının adı.|  
|TABLE_NAME|Dize|Kısıtlama tanımıyla tablonun adı.|  
|COLUMN_NAME|Dize|Sütun veya kısıtlama tanımında belirtilen nesne türü sütununun adı.|  
|KONUMU|Ondalık|Özgün konumu sütun ya da öznitelik nesnesinin tanımı.|  
  
## <a name="procedureparameters"></a>ProcedureParameters  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Nesnenin sahibi.|  
|OBJECT_NAME|Dize|Yordam veya işlev adı.|  
|PAKET_ADI|Dize|Yordam veya işlev adı.|  
|OBJECT_ID|Ondalık|Nesne nesne sayısı.|  
|AŞIRI YÜKLEME|Dize|Benzersiz tanımlayıcı aşırı yükleme.|  
|ARGUMENT_NAME|Dize|Bağımsız değişken adı.|  
|KONUMU|Ondalık|Konum bağımsız değişken listesi veya bir işlevin dönüş değeri null.|  
|SIRASI|Ondalık|Tüm iç içe geçme düzeyi de dahil olmak üzere, bağımsız değişken dizisi.|  
|DATA_LEVEL|Ondalık|Bileşik türler için bağımsız değişken derinliği iç içe geçme.|  
|DATA_TYPE|Dize|Bağımsız değişken veri türü.|  
|DEFAULT_VALUE|Dize|Bağımsız değişkeni için varsayılan değer.|  
|DEFAULT_LENGTH|Ondalık|Bağımsız değişkeni için varsayılan değer uzunluğu.|  
|IN_OUT|Dize|Bağımsız değişken yönü (İNÇ, çıkış veya giriş/çıkış).|  
|DATA_LENGTH|Ondalık|(Bayt cinsinden) sütun uzunluğu.|  
|DATA_PRECISION|Ondalık|Ondalık sayılar (sayı) veya ikili basamak (kayan nokta) cinsinden uzunluğu.|  
|DATA_SCALE|Ondalık|Basamaklı bir sayı ondalık konumun sağında.|  
|SAYI TABANINI|Ondalık|Bağımsız değişken taban sayısı için.|  
|CHARACTER_SET_NAME|Dize|Karakter kümesi adı bağımsız değişkeni.|  
|TYPE_OWNER|Dize|Bağımsız değişken türü sahibi.|  
|TYPE_NAME|Dize|Bağımsız değişkenin türünün adı. Tür bir paket yerel türü ise (diğer bir deyişle, bu bir paket belirtiminde bildirilmiş), bu sütun paketinin adını görüntüler.|  
|TYPE_SUBNAME|Dize|Paket yerel türleri için yalnızca ilgili. TYPE_NAME sütununda tanımlanan paketinde bildirilen türü adını görüntüler.|  
|TYPE_LINK|Dize|Uzak bir paket TYPE_NAME sütununda tanımlanan paketi olduğunda, yalnızca paketi yerel türleri için ilgili. Bu sütunu uzak pakete başvurmak için kullanılan veritabanı bağlantısı görüntüler.|  
|PLS_TYPE|Dize|Sayısal bağımsız değişkenleri, bağımsız değişkenin PL/SQL türünün adı. Aksi durumda null.|  
|CHAR_LENGTH|Ondalık|Dize veri türleri için karakter sınırı.|  
|CHAR_USED|Dize|Bayt (B) veya char sınırı (C) dizesi resmi olup olmadığını gösterir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
