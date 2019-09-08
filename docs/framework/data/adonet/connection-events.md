---
title: Bağlantı Olayları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: e958c96e304962dace72e90b9266b57943f01ac9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785739"
---
# <a name="connection-events"></a>Bağlantı Olayları
.NET Framework veri sağlayıcılarının tümünde, bir veri kaynağından bilgilendirici iletileri almak veya bir **bağlantının** durumunun değişip değişmediğini öğrenmek için kullanabileceğiniz iki olayla birlikte **bağlantı** nesneleri vardır. Aşağıdaki tabloda **bağlantı** nesnesinin olayları açıklanmaktadır.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|**Bilgi Iletisi**|Bir veri kaynağından bir bilgi iletisi döndürüldüğünde oluşur. Bilgilendirici mesajlar bir veri kaynağından alınan ve bir özel durum oluşmasına neden olmayan iletilerdir.|  
|**Olayına**|**Bağlantının** durumu değiştiğinde gerçekleşir.|  
  
## <a name="working-with-the-infomessage-event"></a>InfoMessage olayı ile çalışma  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Nesne olayını<xref:System.Data.SqlClient.SqlConnection> kullanarak bir SQL Server veri kaynağından uyarılar ve bilgilendirici iletiler alabilirsiniz. 16 ile 16 arasında önem düzeyine sahip veri kaynağından döndürülen hatalar bir özel durumun oluşturulmasına neden olur. <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Ancak olay, bir hatayla ilişkilendirilmemiş veri kaynağından iletiler almak için kullanılabilir. Microsoft SQL Server durumda, önem derecesi 10 veya daha az olan herhangi bir hata bilgilendirici bir ileti olarak kabul edilir ve <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay kullanılarak yakalanabilir. Daha fazla bilgi için bkz. [veritabanı altyapısı hata önem özellikleri](/sql/relational-databases/errors-events/database-engine-error-severities) makalesi.
  
 Olay, Errors özelliğinde <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> , veri kaynağından gelen iletilerin bir koleksiyonunu içeren bir nesne alır. <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Hata numarası ve ileti metninin yanı sıra hatanın kaynağı için bu koleksiyondaki **hata** nesnelerini sorgulayabilirsiniz. SQL Server .NET Framework Veri Sağlayıcısı veritabanı, saklı yordam ve iletinin geldiği satır numarası hakkında ayrıntı de içerir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay için bir olay işleyicisinin nasıl ekleneceğini gösterir.  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=   
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,   
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a>Bilgi Iletileri olarak hataları işleme  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Olay normalde yalnızca sunucudan gönderilen bilgilendirici ve uyarı iletileri için harekete geçmeyecektir. Ancak, gerçek bir hata oluştuğunda, sunucu işlemini başlatan **ExecuteNonQuery** veya **ExecuteReader** yönteminin yürütülmesi durdurulur ve bir özel durum oluşturulur.  
  
 Sunucu tarafından üretilen hatalardan bağımsız olarak bir komutta geri kalan deyimlerin işlenmesine devam etmek istiyorsanız, <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> <xref:System.Data.SqlClient.SqlConnection> öğesinin özelliğini olarak `true`ayarlayın. Bunun yapılması bağlantının özel durum oluşturmak ve işlemeyi <xref:System.Data.SqlClient.SqlConnection.InfoMessage> kesintiye uğratma yerine olayı hatalara karşı tetiklenmesine neden olur. İstemci uygulaması daha sonra bu olayı işleyebilir ve hata koşullarına yanıt verebilir.  
  
> [!NOTE]
> Sunucunun işlemeyi durdurmasına neden olan 17 veya üzeri önem düzeyine sahip bir hata, bir özel durum olarak işlenmelidir. Bu durumda, hatanın <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olayda nasıl işlendiğine bakılmaksızın bir özel durum oluşturulur.  
  
## <a name="working-with-the-statechange-event"></a>StateChange olayından çalışma  
 **StateChange** olayı, bir **bağlantının** durumu değiştiğinde oluşur. Bu, **OriginalState** ve **CurrentState** özelliklerini kullanarak **bağlantı** durumundaki değişikliği belirlemenizi sağlayan **StateChange** olayı alır <xref:System.Data.StateChangeEventArgs> . **OriginalState** özelliği, **bağlantı** değiştirilmeden <xref:System.Data.ConnectionState> önceki durumunu gösteren bir numaralandırmadır. **CurrentState** , bağlantı <xref:System.Data.ConnectionState> değiştirildikten sonra **bağlantının** durumunu gösteren bir numaralandırmadır.  
  
 Aşağıdaki kod örneği, **bağlantının** durumu değiştiğinde konsola bir ileti yazmak için **StateChange** olayını kullanır.  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,   
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Kaynağına Bağlanma](connecting-to-a-data-source.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
