---
title: Bağlantı Olayları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: 8ed62d0193639b434d66c446e3b9d0c184577a80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949556"
---
# <a name="connection-events"></a><span data-ttu-id="71e55-102">Bağlantı Olayları</span><span class="sxs-lookup"><span data-stu-id="71e55-102">Connection Events</span></span>
<span data-ttu-id="71e55-103">.NET Framework veri sağlayıcılarının tümünde, bir veri kaynağından bilgilendirici iletileri almak veya bir **bağlantının** durumunun değişip değişmediğini öğrenmek için kullanabileceğiniz iki olayla birlikte **bağlantı** nesneleri vardır.</span><span class="sxs-lookup"><span data-stu-id="71e55-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="71e55-104">Aşağıdaki tabloda **bağlantı** nesnesinin olayları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="71e55-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="71e55-105">Olay</span><span class="sxs-lookup"><span data-stu-id="71e55-105">Event</span></span>|<span data-ttu-id="71e55-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71e55-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71e55-107">**Bilgi Iletisi**</span><span class="sxs-lookup"><span data-stu-id="71e55-107">**InfoMessage**</span></span>|<span data-ttu-id="71e55-108">Bir veri kaynağından bir bilgi iletisi döndürüldüğünde oluşur.</span><span class="sxs-lookup"><span data-stu-id="71e55-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="71e55-109">Bilgilendirici mesajlar bir veri kaynağından alınan ve bir özel durum oluşmasına neden olmayan iletilerdir.</span><span class="sxs-lookup"><span data-stu-id="71e55-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="71e55-110">**Olayına**</span><span class="sxs-lookup"><span data-stu-id="71e55-110">**StateChange**</span></span>|<span data-ttu-id="71e55-111">**Bağlantının** durumu değiştiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="71e55-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="71e55-112">InfoMessage olayı ile çalışma</span><span class="sxs-lookup"><span data-stu-id="71e55-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="71e55-113"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Nesne olayını<xref:System.Data.SqlClient.SqlConnection> kullanarak bir SQL Server veri kaynağından uyarılar ve bilgilendirici iletiler alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71e55-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="71e55-114">16 ile 16 arasında önem düzeyine sahip veri kaynağından döndürülen hatalar bir özel durumun oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="71e55-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="71e55-115"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Ancak olay, bir hatayla ilişkilendirilmemiş veri kaynağından iletiler almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71e55-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="71e55-116">Microsoft SQL Server durumda, önem derecesi 10 veya daha az olan herhangi bir hata bilgilendirici bir ileti olarak kabul edilir ve <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay kullanılarak yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="71e55-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="71e55-117">Daha fazla bilgi için bkz. [veritabanı altyapısı hata önem özellikleri](/sql/relational-databases/errors-events/database-engine-error-severities) makalesi.</span><span class="sxs-lookup"><span data-stu-id="71e55-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="71e55-118">Olay, Errors özelliğinde <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> , veri kaynağından gelen iletilerin bir koleksiyonunu içeren bir nesne alır. <xref:System.Data.SqlClient.SqlConnection.InfoMessage></span><span class="sxs-lookup"><span data-stu-id="71e55-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="71e55-119">Hata numarası ve ileti metninin yanı sıra hatanın kaynağı için bu koleksiyondaki **hata** nesnelerini sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71e55-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="71e55-120">SQL Server .NET Framework Veri Sağlayıcısı veritabanı, saklı yordam ve iletinin geldiği satır numarası hakkında ayrıntı de içerir.</span><span class="sxs-lookup"><span data-stu-id="71e55-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="71e55-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="71e55-121">Example</span></span>  
 <span data-ttu-id="71e55-122">Aşağıdaki kod örneği, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay için bir olay işleyicisinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="71e55-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
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
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="71e55-123">Bilgi Iletileri olarak hataları işleme</span><span class="sxs-lookup"><span data-stu-id="71e55-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="71e55-124"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Olay normalde yalnızca sunucudan gönderilen bilgilendirici ve uyarı iletileri için harekete geçmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="71e55-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="71e55-125">Ancak, gerçek bir hata oluştuğunda, sunucu işlemini başlatan **ExecuteNonQuery** veya **ExecuteReader** yönteminin yürütülmesi durdurulur ve bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="71e55-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="71e55-126">Sunucu tarafından üretilen hatalardan bağımsız olarak bir komutta geri kalan deyimlerin işlenmesine devam etmek istiyorsanız, <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> <xref:System.Data.SqlClient.SqlConnection> öğesinin özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="71e55-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="71e55-127">Bunun yapılması bağlantının özel durum oluşturmak ve işlemeyi <xref:System.Data.SqlClient.SqlConnection.InfoMessage> kesintiye uğratma yerine olayı hatalara karşı tetiklenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="71e55-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="71e55-128">İstemci uygulaması daha sonra bu olayı işleyebilir ve hata koşullarına yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="71e55-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71e55-129">Sunucunun işlemeyi durdurmasına neden olan 17 veya üzeri önem düzeyine sahip bir hata, bir özel durum olarak işlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="71e55-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="71e55-130">Bu durumda, hatanın <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olayda nasıl işlendiğine bakılmaksızın bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="71e55-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="71e55-131">StateChange olayından çalışma</span><span class="sxs-lookup"><span data-stu-id="71e55-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="71e55-132">**StateChange** olayı, bir **bağlantının** durumu değiştiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="71e55-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="71e55-133">Bu, **OriginalState** ve **CurrentState** özelliklerini kullanarak **bağlantı** durumundaki değişikliği belirlemenizi sağlayan **StateChange** olayı alır <xref:System.Data.StateChangeEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="71e55-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="71e55-134">**OriginalState** özelliği, **bağlantı** değiştirilmeden <xref:System.Data.ConnectionState> önceki durumunu gösteren bir numaralandırmadır.</span><span class="sxs-lookup"><span data-stu-id="71e55-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="71e55-135">**CurrentState** , bağlantı <xref:System.Data.ConnectionState> değiştirildikten sonra **bağlantının** durumunu gösteren bir numaralandırmadır.</span><span class="sxs-lookup"><span data-stu-id="71e55-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="71e55-136">Aşağıdaki kod örneği, **bağlantının** durumu değiştiğinde konsola bir ileti yazmak için **StateChange** olayını kullanır.</span><span class="sxs-lookup"><span data-stu-id="71e55-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="71e55-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71e55-137">See also</span></span>

- [<span data-ttu-id="71e55-138">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="71e55-138">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="71e55-139">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="71e55-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
