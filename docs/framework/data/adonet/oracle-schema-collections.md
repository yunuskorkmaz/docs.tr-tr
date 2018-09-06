---
title: Oracle şema koleksiyonları
ms.date: 03/30/2017
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
ms.openlocfilehash: 342c4cbe994eb983713be0f258e3a029df6739f8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886090"
---
# <a name="oracle-schema-collections"></a>Oracle şema koleksiyonları
Oracle için Microsoft .NET Framework veri sağlayıcısı, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:  
  
-   Sütunlar  
  
-   Dizinleri  
  
-   IndexColumns  
  
-   Yordamlar  
  
-   Diziler  
  
-   Eş anlamlıları  
  
-   Tabloları  
  
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
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Tablo, görünüm veya kümesinin sahibi.|  
|TABLE_NAME|Dize|Tablo, görünüm veya küme adı.|  
|COLUMN_NAME|Dize|Sütun adı.|  
|Kimlik|Ondalık|Sütun sayısı, oluşturulan olarak sıralayın.|  
|VERİ TÜRÜ|Dize|Sütunun veri türü.|  
|UZUNLUĞU|Ondalık|Sütun bayt cinsinden uzunluğu.|  
|DUYARLIK|Ondalık|Sayı veri türü için Ondalık Duyarlığı; ikili duyarlık kayan veri türü, null için diğer veri türleri için.|  
|ÖLÇEK|Ondalık|Bir sayı ondalık noktasının sağındaki basamak.|  
|BOŞ DEĞER ATANABİLİR|Dize|Bir sütunu null değerlere izin verip vermediğini belirtir. Değer N sütunu bir NOT NULL kısıtlaması varsa veya sütun birincil ANAHTARIN parçası ise.|  
  
## <a name="indexes"></a>Dizinleri  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Sahip dizini|  
|INDEX_NAME|Dize|Dizinin adı.|  
|INDEX_TYPE|Dize|Dizin (NORMAL, bit eşlem, NORMAL işlev tabanlı, bit eşlem işlevi tabanlı veya etki alanı) türü.|  
|TABLE_OWNER|Dize|Dizinli nesnenin sahibi.|  
|TABLE_NAME|Dize|Dizinli nesnesinin adı.|  
|TABLE_TYPE|Dize|(Örneğin, tablo, küme) dizini oluşturulan nesnenin türü.|  
|BENZERSİZLİK|Dize|Dizini benzersiz veya NONUNIQUE olup olmadığı.|  
|SIKIŞTIRMA|Dize|Dizin etkin veya devre dışı olup olmadığı.|  
|PREFIX_LENGTH|Ondalık|Önek sıkıştırma anahtar sütun sayısı.|  
|TABLESPACE_NAME|Dize|Dizin içeren tablo adı.|  
|INI_TRANS|Ondalık|İlk işlem sayısı.|  
|MAX_TRANS|Ondalık|En fazla işlem sayısı.|  
|INITIAL_EXTENT|Ondalık|İlk kapsamın boyutu.|  
|NEXT_EXTENT|Ondalık|İkincil yerleşimi boyutu.|  
|MIN_EXTENTS|Ondalık|Kapsam segment izin verilen en düşük sayısı.|  
|MAX_EXTENTS|Ondalık|Kapsam segment izin verilen en fazla sayısı.|  
|PCT_INCREASE|Ondalık|Kapsam boyutunu artış yüzdesi.|  
|PCT_THRESHOLD|Ondalık|Dizin girdisi izin verilen blok alan yüzdesi eşiği.|  
|INCLUDE_COLUMN|Ondalık|Dizini düzenlenmiş tabloda birincil anahtar (taşma olmayan) dizine dahil edilecek sütun kimliği son sütunu. Bu sütun için COLUMN_ID sütununun eşler * _TAB_COLUMNS veri sözlüğü görünümleri.|  
|LİSTE|Ondalık|Bu kesimin için ayrılan işlem liste sayısı.|  
|FREELIST_GROUPS|Ondalık|Bu kesimin için ayrılan freelist grubu sayısı.|  
|PCT_FREE|Ondalık|Boş bir blok içindeki minimum yüzdesi.|  
|GÜNLÜĞE KAYDETME|Dize|Günlük bilgileri.|  
|BLEVEL|Ondalık|B *-Ağaç düzeyi: yaprak bloklarla kendi kök bloğunun dizine derinliği. 0 derinliğini kök bloğu ve yaprak bloğu aynı olduğunu gösterir.|  
|LEAF_BLOCKS|Ondalık|Dizin içindeki yaprak bloğu sayısı.|  
|DISTINCT_KEYS|Ondalık|Farklı dizinli değerlerinin sayısı. BENZERSİZ ve PRIMARY KEY kısıtlamaları zorunlu kılma dizinleri için bu değeri (USER_TABLES. tablodaki satır sayısını aynıdır NUM_ROWS).|  
|AVG_LEAF_BLOCKS_PER_KEY|Ondalık|Dizindeki her benzersiz değer göründüğü yaprak blokların en yakın tamsayıya yuvarlanır ortalama sayısı. BENZERSİZ ve PRIMARY KEY kısıtlamaları zorunlu kılma dizinleri için bu değer her zaman 1'dir.|  
|AVG_DATA_BLOCKS_PER_KEY|Ondalık|Farklı bir değer en yakın tamsayıya yuvarlanır dizindeki işaret ettiği tabloda veri ortalama sayısıdır engeller. Bu istatistik dizinli sütunlar için belirli bir değer içeren satırları içeren veri bloklarını ortalama sayısıdır.|  
|CLUSTERING_FACTOR|Ondalık|Dizin değerlerine göre tablosundaki satırları sırasını gösterir.|  
|DURUMU|Dize|Bölümlenmemişse dizini geçerli veya UNUSABLE olup olmadığı.|  
|NUM_ROWS|Ondalık|Dizin içinde satır sayısını belirtir.|  
|SAMPLE_SIZE|Ondalık|Dizin analiz etmek için kullanılan örnek boyutu.|  
|LAST_ANALYZED|DateTime|Bu dizini en yakın zamanda çözümlendi tarih.|  
|DERECE|Dize|Dizin tarama için örnek başına iş parçacığı sayısı.|  
|ÖRNEKLERİ|Dize|Hangi örneklerinde sayısı taranacak dizinler.|  
|BÖLÜMLENMİŞ|Dize|Bu dizin olup bölümlenen (Evet &#124; yok).|  
|GEÇİCİ|Dize|Dizin geçici bir tablo olup olmadığı.|  
|OLUŞTURULAN|Dize|Dizin adı sistem tarafından oluşturulan olup (Y&#124;N).|  
|İKİNCİL|Dize|Dizin Oracle9i veri Kartuş ODCIIndexCreate yöntemi tarafından oluşturulan ikincil bir nesne olup (Y&#124;N).|  
|BUFFER_POOL|Dize|Dizin blokları için kullanılacak varsayılan arabellek havuzunun adı.|  
|USER_STATS|Dize|Olup istatistikleri doğrudan kullanıcı tarafından girilen.|  
|SÜRESİ|Dize|Geçici tablo süresini gösterir: 1) SYS$ oturum: satır 2) SYS$ işlem oturum süresi boyunca korunur: satırları işleme, kalıcı bir tablo için Null 3) sonra silinir.|  
|PCT_DIRECT_ACCESS|Ondalık|İkincil bir dizin için dizin düzenli bir tablosunda, geçerli satırlarla yüzdesini tahmin|  
|ITYP_OWNER|Dize|Etki alanı dizini için indextype sahibi.|  
|ITYP_NAME|Dize|Etki alanı dizini için indextype adı.|  
|PARAMETRELERİ|Dize|Etki alanı dizini için parametre dizesi.|  
|GLOBAL_STATS|Dize|Bölümlenmiş dizinleri için istatistik dizini (Evet) bir bütün olarak incelenerek toplanan veya temel dizin bölümlerini ve subpartitions (Hayır) İstatistikler tahmini gösterir.|  
|DOMIDX_STATUS|Dize|Etki alanı dizini durumunu yansıtır. NULL: Belirtilen dizin, bir etki alanı dizini değil. Geçerli: dizini geçerli bir etki alanı dizini değil. IDXTYP_INVLD: Bu etki alanı dizininin dizin türü geçersiz.|  
|DOMIDX_OPSTATUS|Dize|Bir etki alanı dizini gerçekleştirilen bir işlem durumunu yansıtır: NULL: Belirtilen dizin, bir etki alanı dizini değil. Geçerli: hatasız işlemi gerçekleştirildi. Başarısız oldu: işlem bir hata ile başarısız oldu.|  
|FUNCIDX_STATUS|Dize|İşlev tabanlı bir dizin durumunu gösterir: NULL: Bu işlev tabanlı değil dizin yeniden etkin: işlevi tabanlı bir dizin etkin, devre dışı: işlevi tabanlı dizini devre dışı bırakıldı.|  
|JOIN_INDEX|Dize|Bu bir birleştirme dizin olup olmadığını gösterir.|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|INDEX_OWNER|Dize|Dizin sahibi.|  
|INDEX_NAME|Dize|Dizinin adı.|  
|TABLE_OWNER|Dize|Tablo veya kümesinin sahibi.|  
|TABLE_NAME|Dize|Tablo veya küme adı.|  
|COLUMN_NAME|Dize|Sütun adı veya nesne türü sütunu özniteliği.|  
|COLUMN_POSITION|Ondalık|Sütun veya içinde dizin özniteliği konumu.|  
|COLUMN_LENGTH|Ondalık|Sütun dizini oluşturulmuş uzunluğu.|  
|CHAR_LENGTH|Ondalık|Sütun uzunluğu en fazla kod noktası.|  
|DÜZEN|Dize|Olup sütun azalan düzende sıralanır.|  
  
## <a name="procedures"></a>Yordamlar  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Nesnenin sahibi.|  
|OBJECT_NAME|Dize|Nesnesinin adı.|  
|SUBOBJECT_NAME|Dize|Alt nesneye (örneğin, bölüm) adı.|  
|OBJECT_ID|Ondalık|Nesne sözlük nesnesi sayısı.|  
|DATA_OBJECT_ID|Ondalık|Nesne içeren kesim sözlük nesnesi sayısı.|  
|LAST_DDL_TIME|DateTime|Son değiştirilme (verir ve izinlerinizi dahil) bir DDL komutundan elde edilen nesnenin için zaman damgası.|  
|ZAMAN DAMGASI|Dize|' % S'nesne (karakter veri) belirtimi için zaman damgası.|  
|DURUMU|Dize|Bir nesnenin (geçerli, geçersiz veya yok) durumu.|  
|GEÇİCİ|Dize|Nesne geçici olup (geçerli oturumu bu nesnesinde yerleştirilen veri görebilirsiniz).|  
|OLUŞTURULAN|Dize|Bu nesne sistem tarafından oluşturulan adı neydi? (Y &#124; N).|  
|İKİNCİL|Dize|Bu Oracle9i veri Kartuş ODCIIndexCreate yöntemi tarafından oluşturulan ikincil bir nesne olup olmadığını (Y &#124; N).|  
|OLUŞTURULAN|DateTime|Nesne oluşturulduğu tarih.|  
  
## <a name="sequences"></a>Diziler  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SEQUENCE_OWNER|Dize|Sıranın sahibinin adı.|  
|SEQUENCE_NAME|Dize|Sıra adı.|  
|MIN_VALUE|Ondalık|En küçük değer dizisi.|  
|MAX_VALUE|Ondalık|Dizinin en büyük değer.|  
|INCREMENT_BY|Ondalık|Değer dizisi olarak artırılır.|  
|CYCLE_FLAG|Dize|Sınıra ulaştıktan üzerinde etrafını Sar dizisi.|  
|ORDER_FLAG|Dize|Sıra numaraları sırayla oluşturulur.|  
|CACHE_SIZE|Ondalık|Önbellek için sıra numaralarının sayısı.|  
|LAST_NUMBER|Ondalık|Son dizi diske yazılan numarası. Bir dizi önbelleğe alma, yazılan numarası kullanıp kullanmadığını disk dizisi önbelleğine yerleştirilen son sayıdır. Bu sayı, kullanılan son sıra numarasından daha büyük olması olasıdır.|  
  
## <a name="synonyms"></a>Eş anlamlıları  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Eş anlamlı sahibi.|  
|SYNONYM_NAME|Dize|Eş adı.|  
|TABLE_OWNER|Dize|Anlamlının başvuruda nesnenin sahibi.|  
|TABLE_NAME|Dize|Anlamlının başvuruda nesnesinin adı.|  
|DB_LINK|Dize|Varsa, başvurulan veritabanı bağlantısının adı.|  
  
## <a name="tables"></a>Tabloları  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Tablonun sahibi.|  
|TABLE_NAME|Dize|Tablonun adı.|  
|TÜRÜ|Dize|Tablo türü.|  
  
## <a name="users"></a>Kullanıcılar  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|NAME|Dize|Kullanıcı adı.|  
|Kimlik|Ondalık|Kullanıcı Kimliği sayısı.|  
|CREATEDATE|DateTime|Kullanıcı oluşturma tarihi.|  
  
## <a name="views"></a>Görünümler  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Görünümün sahibi.|  
|VIEW_NAME|Dize|Görünümün adı.|  
|TEXT_LENGTH|Ondalık|Görünüm metnin uzunluğu.|  
|METİN|Dize|Metni görüntüleyin.|  
|TYPE_TEXT_LENGTH|Ondalık|Türü belirtilmiş görünüm türü yan tümcesi uzunluğu.|  
|METİN_TÜRÜ|Dize|Türü belirtilmiş görünüm türü yan tümcesi.|  
|OID_TEXT_LENGTH|Ondalık|Türü belirtilmiş görünüm ile OID yan tümcesi uzunluğu.|  
|OID_TEXT|Dize|Türü belirtilmiş görünüm OID yan TÜMCESİYLE.|  
|VIEW_TYPE_OWNER|Dize|Görünüm türü belirtilmiş görünüm ise Görünüm türü sahibi.|  
|VIEW_TYPE|Dize|Görünüm türü belirtilmiş görünüm ise Görünüm türü.|  
|SUPERVIEW_NAME|Dize|Değerlendirmesi adı.|  
  
## <a name="functions"></a>İşlevler  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Nesnenin sahibi.|  
|OBJECT_NAME|Dize|Nesnesinin adı.|  
|SUBOBJECT_NAME|Dize|Alt nesneye (örneğin, bölüm) adı.|  
|OBJECT_ID|Ondalık|Nesne sözlük nesnesi sayısı.|  
|DATA_OBJECT_ID|Ondalık|Nesne içeren kesim sözlük nesnesi sayısı.|  
|OBJECT_TYPE|Dize|Nesne türü.|  
|OLUŞTURULAN|DateTime|Nesne oluşturulduğu tarih.|  
|LAST_DDL_TIME|DateTime|Son değiştirilme (verir ve izinlerinizi dahil) bir DDL komutundan elde edilen nesnenin için zaman damgası.|  
|ZAMAN DAMGASI|Dize|' % S'nesne (karakter veri) belirtimi için zaman damgası|  
|DURUMU|Dize|Bir nesnenin (geçerli, geçersiz veya yok) durumu.|  
|GEÇİCİ|Dize|Nesne geçici olup (geçerli oturumu bu nesnesinde yerleştirilen veri görebilirsiniz).|  
|OLUŞTURULAN|Dize|Bu nesne sistem tarafından oluşturulan adı neydi? (Y &#124; N).|  
|İKİNCİL|Dize|Bu Oracle9i veri Kartuş ODCIIndexCreate yöntemi tarafından oluşturulan ikincil bir nesne olup olmadığını (Y &#124; N).|  
  
## <a name="packages"></a>Paketler  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Nesnenin sahibi.|  
|OBJECT_NAME|Dize|Nesnesinin adı.|  
|SUBOBJECT_NAME|Dize|Alt nesneye (örneğin, bölüm) adı.|  
|OBJECT_ID|Ondalık|Nesne sözlük nesnesi sayısı.|  
|DATA_OBJECT_ID|Ondalık|Nesne içeren kesim sözlük nesnesi sayısı.|  
|LAST_DDL_TIME|DateTime|Son değiştirilme (verir ve izinlerinizi dahil) bir DDL komutundan elde edilen nesnenin için zaman damgası.|  
|ZAMAN DAMGASI|Dize|' % S'nesne (karakter veri) belirtimi için zaman damgası.|  
|DURUMU|Dize|Bir nesnenin (geçerli, geçersiz veya yok) durumu.|  
|GEÇİCİ|Dize|Nesne geçici olup (geçerli oturumu bu nesnesinde yerleştirilen veri görebilirsiniz).|  
|OLUŞTURULAN|Dize|Bu nesne sistem tarafından oluşturulan adı neydi? (Y &#124; N).|  
|İKİNCİL|Dize|Bu Oracle9i veri Kartuş ODCIIndexCreate yöntemi tarafından oluşturulan ikincil bir nesne olup olmadığını (Y &#124; N).|  
|OLUŞTURULAN|DateTime|Nesne oluşturulduğu tarih.|  
  
## <a name="packagebodies"></a>PackageBodies  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Nesnenin sahibi.|  
|OBJECT_NAME|Dize|Nesnesinin adı.|  
|SUBOBJECT_NAME|Dize|Alt nesneye (örneğin, bölüm) adı.|  
|OBJECT_ID|Ondalık|Nesne sözlük nesnesi sayısı.|  
|DATA_OBJECT_ID|Ondalık|Nesne içeren kesim sözlük nesnesi sayısı.|  
|LAST_DDL_TIME|DateTime|Son değiştirilme (verir ve izinlerinizi dahil) bir DDL komutundan elde edilen nesnenin için zaman damgası.|  
|ZAMAN DAMGASI|Dize|' % S'nesne (karakter veri) belirtimi için zaman damgası.|  
|DURUMU|Dize|Bir nesnenin (geçerli, geçersiz veya yok) durumu.|  
|GEÇİCİ|Dize|Nesne geçici olup (geçerli oturumu bu nesnesinde yerleştirilen veri görebilirsiniz).|  
|OLUŞTURULAN|Dize|Bu nesne sistem tarafından oluşturulan adı neydi? (Y &#124; N).|  
|İKİNCİL|Dize|Bu Oracle9i veri Kartuş ODCIIndexCreate yöntemi tarafından oluşturulan ikincil bir nesne olup olmadığını (Y &#124; N).|  
|OLUŞTURULAN|DateTime|Nesne oluşturulduğu tarih.|  
  
## <a name="arguments"></a>Arguments  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Nesnenin sahibi adı.|  
|PACKAGE_NAME|Dize|Paket adı.|  
|OBJECT_NAME|Dize|Yordam veya işlevin adı.|  
|ARGUMENT_NAME|Dize|Bağımsız değişkenin adı.|  
|KONUMU|Ondalık|İşlev dönüş değeri için konum bağımsız değişken listesi veya NULL.|  
|DİZİSİ|Ondalık|Tüm iç içe geçme düzeylerini dahil olmak üzere, bağımsız değişken dizisi.|  
|DEFAULT_VALUE|Dize|Bağımsız değişkeni için varsayılan değer.|  
|DEFAULT_LENGTH|Ondalık|Bağımsız değişkeni için varsayılan değerin uzunluğu.|  
|IN_OUT|Dize|Bağımsız değişken yönü (IN, OUT veya IN/OUT).|  
|DATA_LENGTH|Ondalık|Sütun bayt cinsinden uzunluğu.|  
|DATA_PRECISION|Ondalık|Ondalık basamak (sayı) veya ikili basamak (FLOAT) cinsinden uzunluğu.|  
|DATA_SCALE|Ondalık|Bir sayı ondalık noktasının sağındaki basamak.|  
|DATA_TYPE|Dize|Bağımsız değişkenin veri türü.|  
  
## <a name="uniquekeys"></a>UniqueKeys  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Kısıtlama tanımının sahibi.|  
|CONSTRAINT_NAME|Dize|Kısıtlama tanımının adı.|  
|TABLE_NAME|Dize|Tablo (veya Görünüm) ile kısıtlaması tanımıyla ilişkili ad.|  
|SEARCH_CONDITION|Dize|Bir denetim kısıtlaması için arama koşulunu metni.|  
|R_OWNER|Dize|Tablonun sahibi için bir başvuru kısıtlamasındaki denir.|  
|R_CONSTRAINT_NAME|Dize|Başvurulan tablo için benzersiz kısıtlama tanımının adı.|  
|DELETE_RULE|Dize|Kural için bir başvuru kısıtlamasını (art ARDA veya eylem yok) silin.|  
|DURUMU|Dize|(Etkin veya devre dışı) kısıtlaması zorlama durumu.|  
|DEFERRABLE|Dize|Kısıtlama deferrable olup olmadığı.|  
|DOĞRULANDI|Dize|Olup tüm verileri (veya DOĞRULANMAMIŞ DOĞRULANACAĞINI) kısıtlama ilişkiden.|  
|OLUŞTURULAN|Dize|Kısıtlama adı kullanıcı veya sistem tarafından oluşturulan olup olmadığı.|  
|HATALI|Dize|Bu kısıtlama, belirsiz bir şekilde bir yüzyıl belirtir Evet değeri gösterir. Bu belirsizlik işlemler sırasında kaynaklanan hataları önlemek için kısıtlaması ile birlikte dört haneli yıla TO_DATE işlevi kullanarak yeniden yazın.|  
|KULLANAN|Dize|Olup etkinleştirilmiş bir kısıtlama zorlanan zorlanmamış veya.|  
|LAST_CHANGE|DateTime|Ne zaman kısıtlaması en son etkin veya devre dışı|  
|INDEX_OWNER|Dize|Dizine sahip olan kullanıcı adı|  
|INDEX_NAME|Dize|Dizinin adı|  
  
## <a name="primarykeys"></a>PrimaryKeys  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Kısıtlama tanımının sahibi.|  
|CONSTRAINT_NAME|Dize|Kısıtlama tanımının adı.|  
|TABLE_NAME|Dize|Tablo (veya Görünüm) ile kısıtlaması tanımıyla ilişkili ad.|  
|SEARCH_CONDITION|Dize|Bir denetim kısıtlaması için arama koşulunu metni.|  
|R_OWNER|Dize|Tablonun sahibi için bir başvuru kısıtlamasındaki denir.|  
|R_CONSTRAINT_NAME|Dize|Başvurulan tablo için benzersiz kısıtlama tanımının adı.|  
|DELETE_RULE|Dize|Kural için bir başvuru kısıtlamasını (art ARDA veya eylem yok) silin.|  
|DURUMU|Dize|(Etkin veya devre dışı) kısıtlaması zorlama durumu.|  
|DEFERRABLE|Dize|Kısıtlama deferrable olup olmadığı.|  
|DOĞRULANDI|Dize|Olup tüm verileri (veya DOĞRULANMAMIŞ DOĞRULANACAĞINI) kısıtlama ilişkiden.|  
|OLUŞTURULAN|Dize|Kısıtlama adı kullanıcı veya sistem tarafından oluşturulan olup olmadığı.|  
|HATALI|Dize|Bu kısıtlama, belirsiz bir şekilde bir yüzyıl belirtir Evet değeri gösterir. Bu belirsizlik işlemler sırasında kaynaklanan hataları önlemek için kısıtlaması ile birlikte dört haneli yıla TO_DATE işlevi kullanarak yeniden yazın.|  
|KULLANAN|Dize|Olup etkinleştirilmiş bir kısıtlama zorlanan zorlanmamış veya.|  
|LAST_CHANGE|DateTime|Ne zaman kısıtlaması en son etkin veya devre dışı.|  
|INDEX_OWNER|Dize|Dizine sahip olan kullanıcı adı.|  
|INDEX_NAME|Dize|Dizinin adı.|  
  
## <a name="foreignkeys"></a>ForeignKeys  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|PRIMARY_KEY_CONSTRAINT_NAME|Dize|Kısıtlama tanımının adı.|  
|PRIMARY_KEY_OWNER|Dize|Kısıtlama tanımının sahibi.|  
|PRIMARY_KEY_TABLE_NAME|Dize|Tablo (veya Görünüm) ile kısıtlaması tanımıyla ilişkili ad|  
|FOREIGN_KEY_OWNER|Dize|Kısıtlama tanımının sahibi.|  
|FOREIGN_KEY_CONSTRIANT_NAME|Dize|Kısıtlama tanımının adı.|  
|FOREIGN_KEY_TABLE_NAME|Dize|Tablo (veya Görünüm) ile kısıtlaması tanımıyla ilişkili ad.|  
|SEARCH_CONDITION|Dize|Bir denetim kısıtlaması için arama koşulunu metni|  
|R_OWNER|Dize|Tablonun sahibi için bir başvuru kısıtlamasındaki denir.|  
|R_CONSTRAINT_NAME|Dize|Başvurulan tablo için benzersiz kısıtlama tanımının adı.|  
|DELETE_RULE|Dize|Kural için bir başvuru kısıtlamasını (art ARDA veya eylem yok) silin.|  
|DURUMU|Dize|(Etkin veya devre dışı) kısıtlaması zorlama durumu.|  
|DOĞRULANDI|Dize|Olup tüm verileri (veya DOĞRULANMAMIŞ DOĞRULANACAĞINI) kısıtlama ilişkiden.|  
|OLUŞTURULAN|Dize|Kısıtlama adı kullanıcı veya sistem tarafından oluşturulan olup olmadığı.|  
|KULLANAN|Dize|Olup etkinleştirilmiş bir kısıtlama zorlanan zorlanmamış veya.|  
|LAST_CHANGE|DateTime|Ne zaman kısıtlaması en son etkin veya devre dışı.|  
|INDEX_OWNER|Dize|Dizine sahip olan kullanıcı adı.|  
|INDEX_NAME|Dize|Dizinin adı.|  
  
## <a name="foreignkeycolumns"></a>ForeignKeyColumns  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Kısıtlama tanımının sahibi.|  
|CONSTRAINT_NAME|Dize|Kısıtlama tanımının adı.|  
|TABLE_NAME|Dize|Kısıtlama tanımıyla tablosunun adı.|  
|COLUMN_NAME|Dize|Sütun veya öznitelik kısıtlaması tanımında belirtilen nesne türü sütununun adı.|  
|KONUMU|Ondalık|Özgün konumu sütun veya öznitelik nesnesinin tanımı.|  
  
## <a name="procedureparameters"></a>ProcedureParameters  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SAHİBİ|Dize|Nesnenin sahibi.|  
|OBJECT_NAME|Dize|Yordam veya işlevin adı.|  
|PACKAGE_NAME|Dize|Yordam veya işlevin adı.|  
|OBJECT_ID|Ondalık|Nesne nesnesi sayısı.|  
|AŞIRI YÜKLEME|Dize|Benzersiz tanımlayıcı aşırı yükleme.|  
|ARGUMENT_NAME|Dize|Bağımsız değişkenin adı.|  
|KONUMU|Ondalık|Konum bağımsız değişken listesi veya bir işlev dönüş değeri null.|  
|DİZİSİ|Ondalık|Tüm iç içe geçme düzeylerini dahil olmak üzere, bağımsız değişken dizisi.|  
|DATA_LEVEL|Ondalık|Bileşik türler için bağımsız değişken derinliğini iç içe geçirme.|  
|DATA_TYPE|Dize|Bağımsız değişkenin veri türü.|  
|DEFAULT_VALUE|Dize|Bağımsız değişkeni için varsayılan değer.|  
|DEFAULT_LENGTH|Ondalık|Bağımsız değişkeni için varsayılan değerin uzunluğu.|  
|IN_OUT|Dize|Bağımsız değişken yönü (IN, OUT veya IN/OUT).|  
|DATA_LENGTH|Ondalık|Uzunluğu (bayt cinsinden) sütunu.|  
|DATA_PRECISION|Ondalık|Ondalık basamak (sayı) veya ikili basamak (FLOAT) cinsinden uzunluğu.|  
|DATA_SCALE|Ondalık|Bir sayı ondalık noktasının sağındaki basamak.|  
|SAYI TABANI|Ondalık|Bağımsız değişken tabanı için bir sayı.|  
|CHARACTER_SET_NAME|Dize|Karakter kümesi bağımsız değişkeni adı.|  
|TYPE_OWNER|Dize|Bağımsız değişken türünü sahibi.|  
|TYPE_NAME|Dize|Bağımsız değişkenin türünün adı. Tür paketini yerel bir tür ise (diğer bir deyişle, bir paket belirtiminde bildirildiği), bu sütun paketinin adını görüntüler.|  
|TYPE_SUBNAME|Dize|Yalnızca yerel paket türleri için ilgili. TYPE_NAME sütununda tanımlanan paketinde bildirilen türü adını görüntüler.|  
|TYPE_LINK|Dize|Uzak bir paket TYPE_NAME sütununda tanımlanan paketi olduğunda yalnızca paket yerel türleri için ilgili. Bu sütun uzak paketine başvurmak için kullanılan veritabanı bağlantısını görüntüler.|  
|PLS_TYPE|Dize|Sayısal bağımsız değişkenleri, bağımsız değişkenin PL/SQL türünün adı. Aksi durumda null.|  
|CHAR_LENGTH|Ondalık|Dize veri türleri için karakter sınırı.|  
|CHAR_USED|Dize|Bayt (B) veya char sınırı (C) dizesi resmi olup olmadığını belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
