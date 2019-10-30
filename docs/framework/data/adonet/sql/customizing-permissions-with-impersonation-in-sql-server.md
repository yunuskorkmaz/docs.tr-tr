---
title: SQL Server'da Kimliğe Bürünme İzinlerini Özelleştirme
ms.date: 03/30/2017
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
ms.openlocfilehash: 0d5e62019ae8806a7a182919fa06819a08d01301
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040447"
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a>SQL Server'da Kimliğe Bürünme İzinlerini Özelleştirme
Birçok uygulama, temel tablolara erişimi kısıtlamak için sahiplik zincirlemeye bağlı olarak verilere erişmek için saklı yordamlar kullanır. Saklı yordamlar üzerinde yürütme izinleri verebilir, temel tablolarda izinleri iptal edebilir veya reddetmiş olursunuz. SQL Server, saklı yordam ve tablolar aynı sahibe sahip ise çağıranın izinlerini denetlemez. Ancak, nesnelerin farklı sahipleri varsa veya dinamik SQL söz konusu olduğunda sahiplik zincirleme çalışmaz.  
  
 Çağıran tarafından başvurulan veritabanı nesnelerinde izin olmadığında, bir saklı yordamda EXECUTE AS yan tümcesini kullanabilirsiniz. EXECUTE AS yan tümcesinin etkisi, yürütme bağlamının proxy kullanıcısına geçiş yapıdır. Tüm kodun yanı sıra iç içe geçmiş saklı yordamlara veya tetikleyicilere yapılan çağrılar, proxy kullanıcısının güvenlik bağlamı altında yürütülür. Yürütme bağlamı, yalnızca yordamın yürütülmesinden sonra veya bir GERI alma yöntemi verildiğinde özgün çağırana döndürülür.  
  
## <a name="context-switching-with-the-execute-as-statement"></a>EXECUTE AS Ifadesiyle bağlam değiştirme  
 Transact-SQL EXECUTE AS deyimleri, başka bir oturum veya veritabanı kullanıcısını taklit ederek bir deyimin Yürütme bağlamını değiştirmenize olanak sağlar. Bu, sorguları ve yordamları başka bir kullanıcı olarak test etmek için kullanışlı bir tekniktir.  
  
```sql  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 Kimliğe bürünme izniniz olan oturum açma veya Kullanıcı üzerinde KIMLIĞE bürünme izinlerine sahip olmanız gerekir. Bu izin, tüm veritabanları için `sysadmin` ve sahip oldukları veritabanlarındaki rol üyelerini `db_owner` için kapsanır.  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a>EXECUTE AS yan tümcesiyle Izinleri verme  
 Bir saklı yordamın, tetikleyicinin veya Kullanıcı tanımlı işlevin (satır içi tablo değerli işlevler hariç) tanım üstbilgisinde EXECUTE AS yan tümcesini kullanabilirsiniz. Bu, yordamın EXECUTE AS yan tümcesinde belirtilen Kullanıcı adı veya anahtar sözcüğü bağlamında yürütülmesine neden olur. Veritabanında bir oturum açmayla eşlenmemiş bir ara sunucu oluşturabilir ve yalnızca yordam tarafından erişilen nesneler üzerinde gerekli izinleri verebilirsiniz. Yalnızca EXECUTE AS yan tümcesinde belirtilen ara sunucu kullanıcısının, modülün eriştiği tüm nesneler üzerinde izinleri olmalıdır.  
  
> [!NOTE]
> TRUNCATE TABLE gibi bazı eylemlerin tablo izinleri yoktur. Deyimini bir yordam içine ekleyerek ve ALTER TABLE izinlerine sahip bir proxy Kullanıcı belirterek, yordamı yalnızca yordamda yürütme izinleri olan çağıranlar için kesme izinlerini genişletebilirsiniz.  
  
 EXECUTE AS yan tümcesinde belirtilen bağlam, iç içe geçmiş yordamlar ve Tetikleyiciler dahil olmak üzere yordamın süresi için geçerlidir. Yürütme tamamlandığında veya GERI alma açıklaması verildiğinde bağlam çağırana döner.  
  
 Bir yordamda EXECUTE AS yan tümcesini kullanmanın üç adımı vardır.  
  
1. Veritabanında bir oturum açma ile eşlenmeyen bir proxy kullanıcı oluşturun. Bu gerekli değildir, ancak izinleri yönetirken yardımcı olur.  
  
```sql
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1. Proxy kullanıcısına gerekli izinleri verin.  
  
2. EXECUTE AS yan tümcesini saklı yordama veya Kullanıcı tanımlı işleve ekleyin.  
  
```sql
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
> Çağıranın orijinal güvenlik bağlamı korunmadığı için denetim gerektiren uygulamalar kesilebilir. SESSION_USER, USER veya USER_NAME gibi geçerli kullanıcının kimliğini döndüren yerleşik işlevler, özgün çağıranı değil, EXECUTE AS yan tümcesiyle ilişkili kullanıcıyı döndürür.  
  
### <a name="using-execute-as-with-revert"></a>KAPANıRKEN farklı ÇALıŞTıR kullanma  
 Özgün yürütme bağlamına dönmek için Transact-SQL DÖNDÜRÜLÜYOR ifadesini kullanabilirsiniz.  
  
 GERI dönüş tanımlama bilgisi = @variableNameolan isteğe bağlı yan tümce, @variableName değişkeni doğru değeri içeriyorsa, yürütme bağlamını çağırana geri değiştirmenize izin verir. Bu, yürütme bağlamını, bağlantı havuzunun kullanıldığı ortamlarda arayan tarafa geri yüklemenize olanak sağlar. @variableName değeri yalnızca EXECUTE AS deyimlerinin çağıranı tarafından bilindiğinden, çağıran, yürütme bağlamının uygulamayı çağıran Son Kullanıcı tarafından değiştirilemeyeceğini garanti edebilir. Bağlantı kapatıldığında, havuza döndürülür. ADO.NET içinde bağlantı havuzu oluşturma hakkında daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../sql-server-connection-pooling.md).  
  
### <a name="specifying-the-execution-context"></a>Yürütme bağlamını belirtme  
 Bir Kullanıcı belirtmenin yanı sıra, aşağıdaki anahtar kelimelerle de ÇALıŞTıR ' ı da kullanabilirsiniz.  
  
- Yapana. ÇAĞıRAN olarak yürütme varsayılandır; başka bir seçenek belirtilmemişse, yordam çağıranın güvenlik bağlamında yürütülür.  
  
- İnde. SAHIP olarak yürütülerek işlem, yordam sahibi bağlamında yürütülür. Yordam, `dbo` veya veritabanı sahibine ait bir şemada oluşturulduysa, yordam Kısıtlanmamış izinlerle yürütülür.  
  
- Self. , Saklı yordamın oluşturanın güvenlik bağlamında kendi kendine yürütme olarak yürütülür. Bu, belirli bir kullanıcı olarak yürütülene eşdeğerdir; burada belirtilen kullanıcı, yordamı oluşturan veya değiştiren bir kişidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [SQL Server Güvenliğine Genel Bakış](overview-of-sql-server-security.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](application-security-scenarios-in-sql-server.md)
- [SQL Server'da Saklı Yordam İzinlerini Yönetme](managing-permissions-with-stored-procedures-in-sql-server.md)
- [SQL Server’da Secure Dynamic SQL Yazma](writing-secure-dynamic-sql-in-sql-server.md)
- [SQL Server'da Saklı Yordam İmzalama](signing-stored-procedures-in-sql-server.md)
- [Saklı Yordamlarla Verileri Değiştirme](../modifying-data-with-stored-procedures.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
