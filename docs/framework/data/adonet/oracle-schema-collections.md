---
title: Oracle Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
ms.openlocfilehash: cb91a90ae7323283556954caa401646a2063a37e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783289"
---
# <a name="oracle-schema-collections"></a>Oracle Şema Koleksiyonları

Oracle için Microsoft .NET Framework Veri Sağlayıcısı, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:

- Sütunlar

- Dizinlerde

- IndexColumns

- Yordamlar

- Diziler

- Eş anlamlılar

- Takvimleri

- Kullanıcılar

- Görünümler

- İşlevler

- Paketler

- Packagegövdeler

- Arguments

- UniqueKeys

- PrimaryKeys

- Yabancıanahtarlar

- ForeignKeyColumns

- ProcedureParameters

## <a name="columns"></a>Sütunlar

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Tablo, görünüm veya küme sahibi.|
|TABLE_NAME|Dize|Tablo, görünüm veya küme adı.|
|COLUMN_NAME|Dize|Sütun adı.|
|ID|Ondalık|Sütunun oluşturulduğu şekilde sıra numarası.|
|X|Dize|Sütunun veri türü.|
|UZUNLUKLU|Ondalık|Sütunun bayt cinsinden uzunluğu.|
|DUYARLILIK|Ondalık|Sayı veri türü için ondalık duyarlık; FLOAT veri türü için ikili duyarlık, diğer tüm veri türleri için null.|
|ÖLÇEK|Ondalık|Bir sayı içinde ondalık noktanın sağına doğru olan rakamlar.|
|YAPILAMAZ|Dize|Bir sütunun null değerlere izin verip Vermemediğini belirtir. Sütunda NULL olmayan bir kısıtlama varsa veya sütun BIRINCIL ANAHTARıN parçasıysa değer N.|

## <a name="indexes"></a>Dizinlerde

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Dizinin sahibi|
|INDEX_NAME|Dize|Dizinin adı.|
|INDEX_TYPE|Dize|Dizin türü (NORMAL, BIT eşlem, Işlev tabanlı NORMAL, Işlev tabanlı BIT eşlem veya etkı alanı).|
|TABLE_OWNER|Dize|Dizinli nesnenin sahibi.|
|TABLE_NAME|Dize|Dizinli nesnenin adı.|
|TABLE_TYPE|Dize|Dizinli nesnenin türü (örneğin, tablo, küme).|
|KOŞULDAKI|Dize|Dizinin BENZERSIZ mi yoksa BENZERSIZ mi olduğunu belirtir.|
|MASIYLA|Dize|Dizinin ETKIN mi yoksa devre DıŞı mı olduğunu belirtir.|
|PREFIX_LENGTH|Ondalık|Sıkıştırma anahtarının ön ekine ait sütun sayısı.|
|TABLESPACE_NAME|Dize|Dizini içeren tablo alanının adı.|
|INI_TRANS|Ondalık|İlk işlem sayısı.|
|MAX_TRANS|Ondalık|En fazla işlem sayısı.|
|INITIAL_EXTENT|Ondalık|İlk uzantının boyutu.|
|NEXT_EXTENT|Ondalık|İkincil uzantıların boyutu.|
|MIN_EXTENTS|Ondalık|Segmentte izin verilen en az uzantı sayısı.|
|MAX_EXTENTS|Ondalık|Segmentte izin verilen en fazla uzantı sayısı.|
|PCT_INCREASE|Ondalık|Kapsam boyutunun yüzde artışı.|
|PCT_THRESHOLD|Ondalık|Dizin girişi başına izin verilen blok alanı eşik yüzdesi.|
|INCLUDE_COLUMN|Ondalık|Dizin düzenlenmiş tablo birincil anahtar (taşma olmayan) dizinine dahil edilecek son sütunun sütun KIMLIĞI. Bu sütun, * _TAB_COLUMNS veri sözlüğü görünümlerinin COLUMN_ID sütunuyla eşlenir.|
|FREELISTS|Ondalık|Bu kesime ayrılan işlem freelists sayısı.|
|FREELIST_GROUPS|Ondalık|Bu kesime ayrılan freelist gruplarının sayısı.|
|PCT_FREE|Ondalık|Bir bloktaki en az boş alan yüzdesi.|
|AÇMAK|Dize|Günlüğe kaydetme bilgileri.|
|BLEVEL|Ondalık|B *-ağaç düzeyi: kök bloğundan yaprak bloklarına dizinin derinliği. 0 derinliği, kök bloğunun ve yaprak bloğunun aynı olduğunu gösterir.|
|LEAF_BLOCKS|Ondalık|Dizindeki yaprak blok sayısı|
|DISTINCT_KEYS|Ondalık|Farklı dizinli değerlerin sayısı. BENZERSIZ ve BIRINCIL anahtar kısıtlamalarını zorlayan dizinler için, bu değer tablodaki satır sayısıyla aynıdır (USER_TABLES. NUM_ROWS).|
|AVG_LEAF_BLOCKS_PER_KEY|Ondalık|Dizindeki her farklı değerin en yakın tamsayıya yuvarlanır şekilde göründüğü yaprak bloklarının ortalama sayısı. BENZERSIZ ve BIRINCIL anahtar kısıtlamalarını zorlayan dizinler için bu değer her zaman 1 ' dir.|
|AVG_DATA_BLOCKS_PER_KEY|Ondalık|Dizindeki ayrı bir değer tarafından işaret edilen, en yakın tamsayıya yuvarlanan, tablodaki ortalama veri bloğu sayısı. Bu istatistik, dizinli sütunlar için verilen bir değer içeren satırları içeren veri bloklarının ortalama sayısıdır.|
|CLUSTERING_FACTOR|Ondalık|Tablodaki satırların sıralama miktarını, dizinin değerlerine göre gösterir.|
|DURUMLARINA|Dize|Bölümlenmemiş dizinin GEÇERLI veya kullanılamaz durumda olup olmadığı.|
|NUM_ROWS|Ondalık|Dizindeki satır sayısı.|
|SAMPLE_SIZE|Ondalık|Dizini çözümlemek için kullanılan örneğin boyutu.|
|LAST_ANALYZED|DateTime|Bu dizinin en son çözümlenme tarihi.|
|ÖLÇÜDE|Dize|Dizini taramak için örnek başına iş parçacığı sayısı.|
|LARINDA|Dize|Üzerinde taranacak dizinlerin sayısını gösteren örnek sayısı.|
|ILDI|Dize|Bu dizinin bölümlenmiş olup olmadığı (Evet &#124; Hayır).|
|AYIRMAYA|Dize|Dizinin geçici bir tabloda olup olmadığı.|
|ÜRET|Dize|Dizinin adının sistem tarafından oluşturulup oluşturulmayacağını belirtir (Y&#124;N).|
|IK|Dize|Dizinin Oracle9i veri kartuşunu (Y&#124;N) Odcıındexcreate yöntemi tarafından oluşturulan ikincil nesne olup olmadığı.|
|BUFFER_POOL|Dize|Dizin blokları için kullanılacak varsayılan arabellek havuzunun adı.|
|USER_STATS|Dize|İstatistiklerin Kullanıcı tarafından doğrudan girilip girilmediğini belirtir.|
|SÜRENIN|Dize|Geçici bir tablonun süresini gösterir: 1) SYS $ SESSION: Bu satır, oturum süresince saklanır, 2) SYS $ TRANSACTION: satır, IŞLEMEDEN sonra silinir, 3) kalıcı tablo için null.|
|PCT_DIRECT_ACCESS|Ondalık|Dizin düzenlenmiş bir tablodaki ikincil dizin için, GEÇERLI tahminle satır yüzdesi|
|ITYP_OWNER|Dize|Bir etki alanı dizini için, IndexType sahibi.|
|ITYP_NAME|Dize|Bir etki alanı dizini için IndexType adı.|
|PARAMETRELERE|Dize|Bir etki alanı dizini için parametre dizesi.|
|GLOBAL_STATS|Dize|Bölümlenmiş dizinler için, istatistiklerin bir bütün olarak (Evet) çözümlenerek toplandığını veya temel alınan dizin bölümlerindeki ve alt bölümlerdeki istatistiklerden (Hayır) tahmin edilip edilmeyeceğini belirtir.|
|DOMIDX_STATUS|Dize|Etki alanı dizininin durumunu yansıtır. NULL: belirtilen dizin bir etki alanı dizini değil. GEÇERLI: dizin geçerli bir etki alanı dizinidir. IDXTYP_INVLD: Bu etki alanı dizininin Dizin türü geçersiz.|
|DOMIDX_OPSTATUS|Dize|Bir etki alanı dizininde gerçekleştirilen bir işlemin durumunu yansıtır: NULL: belirtilen dizin bir etki alanı dizini değil. GEÇERLI: işlem hata olmadan gerçekleştirildi. Başarısız oldu: işlem bir hata ile başarısız oldu.|
|FUNCIDX_STATUS|Dize|İşlev tabanlı dizinin durumunu gösterir: NULL: Bu bir işlev tabanlı dizin değil, ETKIN: işlev tabanlı dizin etkin, devre DıŞı: işlev tabanlı dizin devre dışı bırakıldı.|
|JOIN_INDEX|Dize|Bunun bir JOIN dizini olup olmadığını gösterir.|

## <a name="indexcolumns"></a>IndexColumns

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDEX_OWNER|Dize|Dizinin sahibi.|
|INDEX_NAME|Dize|Dizinin adı.|
|TABLE_OWNER|Dize|Tablo veya küme sahibi.|
|TABLE_NAME|Dize|Tablonun veya kümenin adı.|
|COLUMN_NAME|Dize|Sütun adı veya nesne türü sütununun özniteliği.|
|COLUMN_POSITION|Ondalık|Dizinin içindeki sütun veya özniteliğin konumu.|
|COLUMN_LENGTH|Ondalık|Sütunun dizini oluşturulmuş uzunluğu.|
|CHAR_LENGTH|Ondalık|Sütunun en büyük kod noktası uzunluğu.|
|AZALMAZ|Dize|Sütunun azalan sırada sıralanıp sıralanmayacağı.|

## <a name="procedures"></a>Yordamlar

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Nesnenin sahibi.|
|OBJECT_NAME|Dize|Nesnenin adı.|
|SUBOBJECT_NAME|Dize|Alt nesne adı (örneğin, Bölüm).|
|OBJECT_ID|Ondalık|Nesnenin sözlük nesne numarası.|
|DATA_OBJECT_ID|Ondalık|Nesneyi içeren segmentin sözlük nesnesi numarası.|
|LAST_DDL_TIME|DateTime|Bir DDL komutundan kaynaklanan nesnenin son değiştirildiği zaman damgası (izin verilen ve iptal edilen dahil).|
|TIMESTAMP|Dize|Nesnenin belirtimi için zaman damgası (karakter verileri).|
|DURUMLARINA|Dize|Nesnenin durumu (GEÇERLI, GEÇERSIZ veya yok).|
|AYIRMAYA|Dize|Nesnenin geçici olup olmadığı (geçerli oturum yalnızca bu nesnenin kendisine yerleştirilmiş verileri görebilir).|
|ÜRET|Dize|Bu nesne sisteminin adı üretildi mi? (Y &#124; N).|
|IK|Dize|Bu, Oracle9i veri kartuşunun Odcıındexcreate yöntemi tarafından oluşturulan ikincil bir nesne olup olmadığı (Y &#124; N).|
|YARATIL|DateTime|Nesnenin oluşturulduğu tarih.|

## <a name="sequences"></a>Diziler

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|SEQUENCE_OWNER|Dize|Dizinin sahibinin adı.|
|SEQUENCE_NAME|Dize|Sıra adı.|
|MIN_VALUE|Ondalık|Sıranın en küçük değeri.|
|MAX_VALUE|Ondalık|Sıranın en büyük değeri.|
|INCREMENT_BY|Ondalık|Dizinin artarak değeri.|
|CYCLE_FLAG|Dize|Sıra, sınır sınırına ulaşılması sırasında kaydırılır.|
|ORDER_FLAG|Dize|Sıra numaraları sırayla oluşturulur.|
|CACHE_SIZE|Ondalık|Önbelleğe eklenecek sıra numarası sayısı.|
|LAST_NUMBER|Ondalık|Diske yazılan son sıra numarası. Bir dizi önbelleğe alma kullanıyorsa diske yazılan sayı, sıra önbelleğine yerleştirilmiş son sayıdır. Bu sayı büyük olasılıkla kullanılan son sıra numarasından daha büyük olabilir.|

## <a name="synonyms"></a>Eş anlamlılar

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Eş anlamlının sahibi.|
|SYNONYM_NAME|Dize|Eş anlamlının adı.|
|TABLE_OWNER|Dize|Eş anlamlı tarafından başvurulan nesnenin sahibi.|
|TABLE_NAME|Dize|Eş anlamlı tarafından başvurulan nesnenin adı.|
|DB_LINK|Dize|Varsa, başvurulan veritabanı bağlantısının adı.|

## <a name="tables"></a>Takvimleri

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Tablonun sahibi.|
|TABLE_NAME|Dize|Tablonun adı.|
|TÜRÜYLE|Dize|Tablo türü.|

## <a name="users"></a>Kullanıcılar

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|NAME|Dize|Kullanıcının adı.|
|ID|Ondalık|Kullanıcının KIMLIK numarası.|
|CREATEDATE|DateTime|Kullanıcı oluşturma tarihi.|

## <a name="views"></a>Görünümler

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Görünümün sahibi.|
|VIEW_NAME|Dize|Görünümün adı.|
|TEXT_LENGTH|Ondalık|Görünüm metninin uzunluğu.|
|TEXT|Dize|Metni görüntüleyin.|
|TYPE_TEXT_LENGTH|Ondalık|Türü belirlenmiş görünümün tür yan tümcesinin uzunluğu.|
|METIN_TÜRÜ|Dize|Türü belirlenmiş görünümün tür tümcesi.|
|OID_TEXT_LENGTH|Ondalık|Türü belirtilmiş görünümün WıTH OID yan tümcesinin uzunluğu.|
|OID_TEXT|Dize|Türü belirtilmiş görünümün OID yan tümcesi.|
|VIEW_TYPE_OWNER|Dize|Görünüm yazılı bir görünüm ise görünümün türü sahibi.|
|VIEW_TYPE|Dize|Görünüm yazılı bir görünüm ise görünümün türü.|
|SUPERVIEW_NAME|Dize|Üst görünümün adı.|

## <a name="functions"></a>İşlevler

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Nesnenin sahibi.|
|OBJECT_NAME|Dize|Nesnenin adı.|
|SUBOBJECT_NAME|Dize|Alt nesne adı (örneğin, Bölüm).|
|OBJECT_ID|Ondalık|Nesnenin sözlük nesne numarası.|
|DATA_OBJECT_ID|Ondalık|Nesneyi içeren segmentin sözlük nesnesi numarası.|
|OBJECT_TYPE|Dize|Nesnenin türü.|
|YARATIL|DateTime|Nesnenin oluşturulduğu tarih.|
|LAST_DDL_TIME|DateTime|Bir DDL komutundan kaynaklanan nesnenin son değiştirildiği zaman damgası (izin verilen ve iptal edilen dahil).|
|TIMESTAMP|Dize|Nesnenin belirtimi için zaman damgası (karakter verileri)|
|DURUMLARINA|Dize|Nesnenin durumu (GEÇERLI, GEÇERSIZ veya yok).|
|AYIRMAYA|Dize|Nesnenin geçici olup olmadığı (geçerli oturum yalnızca bu nesnenin kendisine yerleştirilmiş verileri görebilir).|
|ÜRET|Dize|Bu nesne sisteminin adı üretildi mi? (Y &#124; N).|
|IK|Dize|Bu, Oracle9i veri kartuşunun Odcıındexcreate yöntemi tarafından oluşturulan ikincil bir nesne olup olmadığı (Y &#124; N).|

## <a name="packages"></a>Paketler

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Nesnenin sahibi.|
|OBJECT_NAME|Dize|Nesnenin adı.|
|SUBOBJECT_NAME|Dize|Alt nesne adı (örneğin, Bölüm).|
|OBJECT_ID|Ondalık|Nesnenin sözlük nesne numarası.|
|DATA_OBJECT_ID|Ondalık|Nesneyi içeren segmentin sözlük nesnesi numarası.|
|LAST_DDL_TIME|DateTime|Bir DDL komutundan kaynaklanan nesnenin son değiştirildiği zaman damgası (izin verilen ve iptal edilen dahil).|
|TIMESTAMP|Dize|Nesnenin belirtimi için zaman damgası (karakter verileri).|
|DURUMLARINA|Dize|Nesnenin durumu (GEÇERLI, GEÇERSIZ veya yok).|
|AYIRMAYA|Dize|Nesnenin geçici olup olmadığı (geçerli oturum yalnızca bu nesnenin kendisine yerleştirilmiş verileri görebilir).|
|ÜRET|Dize|Bu nesne sisteminin adı üretildi mi? (Y &#124; N).|
|IK|Dize|Bu, Oracle9i veri kartuşunun Odcıındexcreate yöntemi tarafından oluşturulan ikincil bir nesne olup olmadığı (Y &#124; N).|
|YARATIL|DateTime|Nesnenin oluşturulduğu tarih.|

## <a name="packagebodies"></a>Packagegövdeler

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Nesnenin sahibi.|
|OBJECT_NAME|Dize|Nesnenin adı.|
|SUBOBJECT_NAME|Dize|Alt nesne adı (örneğin, Bölüm).|
|OBJECT_ID|Ondalık|Nesnenin sözlük nesne numarası.|
|DATA_OBJECT_ID|Ondalık|Nesneyi içeren segmentin sözlük nesnesi numarası.|
|LAST_DDL_TIME|DateTime|Bir DDL komutundan kaynaklanan nesnenin son değiştirildiği zaman damgası (izin verilen ve iptal edilen dahil).|
|TIMESTAMP|Dize|Nesnenin belirtimi için zaman damgası (karakter verileri).|
|DURUMLARINA|Dize|Nesnenin durumu (GEÇERLI, GEÇERSIZ veya yok).|
|AYIRMAYA|Dize|Nesnenin geçici olup olmadığı (geçerli oturum yalnızca bu nesnenin kendisine yerleştirilmiş verileri görebilir).|
|ÜRET|Dize|Bu nesne sisteminin adı üretildi mi? (Y &#124; N).|
|IK|Dize|Bu, Oracle9i veri kartuşunun Odcıındexcreate yöntemi tarafından oluşturulan ikincil bir nesne olup olmadığı (Y &#124; N).|
|YARATIL|DateTime|Nesnenin oluşturulduğu tarih.|

## <a name="arguments"></a>Arguments

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Nesnenin sahibinin adı.|
|PACKAGE_NAME|Dize|Paket adı.|
|OBJECT_NAME|Dize|Yordamın veya işlevin adı.|
|ARGUMENT_NAME|Dize|Bağımsız değişkenin adı.|
|YERINE|Ondalık|Bağımsız değişken listesinde konum veya işlev dönüş değeri için NULL.|
|SIRASINA|Ondalık|Tüm iç içe düzeyler dahil bağımsız değişken sırası.|
|DEFAULT_VALUE|Dize|Bağımsız değişken için varsayılan değer.|
|DEFAULT_LENGTH|Ondalık|Bağımsız değişken için varsayılan değer uzunluğu.|
|IN_OUT|Dize|Bağımsız değişken yönü (ın, OUT veya ın/OUT).|
|DATA_LENGTH|Ondalık|Sütunun bayt cinsinden uzunluğu.|
|DATA_PRECISION|Ondalık|Ondalık basamaklar (sayı) veya ikili basamaklar (FLOAT) uzunluğu.|
|DATA_SCALE|Ondalık|Bir sayı içinde ondalık noktanın sağına doğru olan rakamlar.|
|DATA_TYPE|Dize|Bağımsız değişkenin veri türü.|

## <a name="uniquekeys"></a>UniqueKeys

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Kısıtlama tanımının sahibi.|
|CONSTRAINT_NAME|Dize|Kısıtlama tanımının adı.|
|TABLE_NAME|Dize|Kısıtlama tanımıyla tabloyla (veya görünümde) ilişkili ad.|
|SEARCH_CONDITION|Dize|Bir denetim kısıtlamasının arama koşulunun metni.|
|R_OWNER|Dize|Başvuru kısıtlamasında başvurulan tablo sahibi.|
|R_CONSTRAINT_NAME|Dize|Başvurulan tablo için benzersiz kısıtlama tanımının adı.|
|DELETE_RULE|Dize|Başvuru kısıtlamasının kuralını silin (CASCADE veya NO ACTıON).|
|DURUMLARINA|Dize|Kısıtlamanın zorlama durumu (ETKIN veya devre DıŞı).|
|ERTETE|Dize|Kısıtlamanın erteedilip edilmeyeceğini belirtir.|
|DOĞRULANMASI|Dize|Tüm verilerin kısıtlamaya ulanmayacağı (DOĞRULANAN veya DOĞRULANMADı).|
|ÜRET|Dize|Kısıtlamanın adının Kullanıcı veya sistem tarafından oluşturulup oluşturulmayacağını belirtir.|
|HATALI|Dize|Evet değeri, bu kısıtlamanın bir yüzün belirsiz şekilde olduğunu belirtir. Bu belirsizlik nedeniyle oluşan hataları önlemek için, TO_DATE işlevini kullanarak kısıtlamayı dört basamaklı bir yıl ile yeniden yazın.|
|ALMASI|Dize|Etkin bir kısıtlamanın zorlanıp zorlanmayacağı.|
|LAST_CHANGE|DateTime|Kısıtlama en son etkin veya devre dışı olduğunda|
|INDEX_OWNER|Dize|Dizine sahip olan kullanıcının adı|
|INDEX_NAME|Dize|Dizinin adı|

## <a name="primarykeys"></a>PrimaryKeys

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Kısıtlama tanımının sahibi.|
|CONSTRAINT_NAME|Dize|Kısıtlama tanımının adı.|
|TABLE_NAME|Dize|Kısıtlama tanımıyla tabloyla (veya görünümde) ilişkili ad.|
|SEARCH_CONDITION|Dize|Bir denetim kısıtlamasının arama koşulunun metni.|
|R_OWNER|Dize|Başvuru kısıtlamasında başvurulan tablo sahibi.|
|R_CONSTRAINT_NAME|Dize|Başvurulan tablo için benzersiz kısıtlama tanımının adı.|
|DELETE_RULE|Dize|Başvuru kısıtlamasının kuralını silin (CASCADE veya NO ACTıON).|
|DURUMLARINA|Dize|Kısıtlamanın zorlama durumu (ETKIN veya devre DıŞı).|
|ERTETE|Dize|Kısıtlamanın erteedilip edilmeyeceğini belirtir.|
|DOĞRULANMASI|Dize|Tüm verilerin kısıtlamaya ulanmayacağı (DOĞRULANAN veya DOĞRULANMADı).|
|ÜRET|Dize|Kısıtlamanın adının Kullanıcı veya sistem tarafından oluşturulup oluşturulmayacağını belirtir.|
|HATALI|Dize|Evet değeri, bu kısıtlamanın bir yüzün belirsiz şekilde olduğunu belirtir. Bu belirsizlik nedeniyle oluşan hataları önlemek için, TO_DATE işlevini kullanarak kısıtlamayı dört basamaklı bir yıl ile yeniden yazın.|
|ALMASI|Dize|Etkin bir kısıtlamanın zorlanıp zorlanmayacağı.|
|LAST_CHANGE|DateTime|Kısıtlama en son etkin veya devre dışı olduğunda.|
|INDEX_OWNER|Dize|Dizine sahip olan kullanıcının adı.|
|INDEX_NAME|Dize|Dizinin adı.|

## <a name="foreignkeys"></a>Yabancıanahtarlar

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|PRIMARY_KEY_CONSTRAINT_NAME|Dize|Kısıtlama tanımının adı.|
|PRIMARY_KEY_OWNER|Dize|Kısıtlama tanımının sahibi.|
|PRIMARY_KEY_TABLE_NAME|Dize|Kısıtlama tanımıyla tablo (veya Görünüm) ile ilişkili ad|
|FOREIGN_KEY_OWNER|Dize|Kısıtlama tanımının sahibi.|
|FOREIGN_KEY_CONSTRAINT_NAME|Dize|Kısıtlama tanımının adı.|
|FOREIGN_KEY_TABLE_NAME|Dize|Kısıtlama tanımıyla tabloyla (veya görünümde) ilişkili ad.|
|SEARCH_CONDITION|Dize|Bir denetim kısıtlamasının arama koşulunun metni|
|R_OWNER|Dize|Başvuru kısıtlamasında başvurulan tablo sahibi.|
|R_CONSTRAINT_NAME|Dize|Başvurulan tablo için benzersiz kısıtlama tanımının adı.|
|DELETE_RULE|Dize|Başvuru kısıtlamasının kuralını silin (CASCADE veya NO ACTıON).|
|DURUMLARINA|Dize|Kısıtlamanın zorlama durumu (ETKIN veya devre DıŞı).|
|DOĞRULANMASI|Dize|Tüm verilerin kısıtlamaya ulanmayacağı (DOĞRULANAN veya DOĞRULANMADı).|
|ÜRET|Dize|Kısıtlamanın adının Kullanıcı veya sistem tarafından oluşturulup oluşturulmayacağını belirtir.|
|ALMASI|Dize|Etkin bir kısıtlamanın zorlanıp zorlanmayacağı.|
|LAST_CHANGE|DateTime|Kısıtlama en son etkin veya devre dışı olduğunda.|
|INDEX_OWNER|Dize|Dizine sahip olan kullanıcının adı.|
|INDEX_NAME|Dize|Dizinin adı.|

## <a name="foreignkeycolumns"></a>ForeignKeyColumns

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Kısıtlama tanımının sahibi.|
|CONSTRAINT_NAME|Dize|Kısıtlama tanımının adı.|
|TABLE_NAME|Dize|Kısıtlama tanımına sahip tablonun adı.|
|COLUMN_NAME|Dize|Kısıtlama tanımında belirtilen nesne türü sütununun sütun veya özniteliğinin adı.|
|YERINE|Ondalık|Nesnenin tanımındaki sütunun veya özniteliğin orijinal konumu.|

## <a name="procedureparameters"></a>ProcedureParameters

|Tation|DataType|Açıklama|
|----------------|--------------|-----------------|
|INDE|Dize|Nesnenin sahibi.|
|OBJECT_NAME|Dize|Yordamın veya işlevin adı.|
|PACKAGE_NAME|Dize|Yordamın veya işlevin adı.|
|OBJECT_ID|Ondalık|Nesnenin nesne numarası.|
|YÜKLEMEK|Dize|Aşırı yükleme benzersiz tanımlayıcısı.|
|ARGUMENT_NAME|Dize|Bağımsız değişkenin adı.|
|YERINE|Ondalık|Bağımsız değişken listesindeki konum veya bir işlev dönüş değeri için null.|
|SIRASINA|Ondalık|Tüm iç içe düzeyler dahil bağımsız değişken sırası.|
|DATA_LEVEL|Ondalık|Bileşik türlerin bağımsız değişkeninin iç içe geçme derinliği.|
|DATA_TYPE|Dize|Bağımsız değişkenin veri türü.|
|DEFAULT_VALUE|Dize|Bağımsız değişken için varsayılan değer.|
|DEFAULT_LENGTH|Ondalık|Bağımsız değişken için varsayılan değerin uzunluğu.|
|IN_OUT|Dize|Bağımsız değişken yönü (ın, OUT veya ın/OUT).|
|DATA_LENGTH|Ondalık|Sütunun uzunluğu (bayt cinsinden).|
|DATA_PRECISION|Ondalık|Ondalık basamaklar (sayı) veya ikili basamaklar (FLOAT) uzunluğu.|
|DATA_SCALE|Ondalık|Sayıdaki ondalık noktanın sağ tarafındaki rakamlar.|
|TABAN|Ondalık|Sayı için taban bağımsız değişkeni.|
|CHARACTER_SET_NAME|Dize|Bağımsız değişken için karakter kümesi adı.|
|TYPE_OWNER|Dize|Bağımsız değişkenin türünün sahibi.|
|TYPE_NAME|Dize|Bağımsız değişkenin türünün adı. Tür bir paket yerel türüdür (yani bir paket belirtiminde bildirilirse), bu sütunda paketin adı görüntülenir.|
|TYPE_SUBNAME|Dize|Yalnızca paket yerel türleri için geçerlidir. TYPE_NAME sütununda tanımlanan pakette belirtilen türün adını görüntüler.|
|TYPE_LINK|Dize|Yalnızca TYPE_NAME sütununda tanımlanan paket uzak bir paket olduğunda, paket yerel türleri için geçerlidir. Bu sütun, uzak pakete başvurmak için kullanılan veritabanı bağlantısını görüntüler.|
|PLS_TYPE|Dize|Sayısal bağımsız değişkenler için bağımsız değişkenin PL/SQL türünün adı. Aksi durumda null.|
|CHAR_LENGTH|Ondalık|Dize veri türleri için karakter sınırı.|
|CHAR_USED|Dize|Bayt sınırının (B) veya char sınırının (C) dize için resmi olup olmadığını gösterir.|

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](ado-net-overview.md)
