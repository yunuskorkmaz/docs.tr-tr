---
title: "Nasıl yapılır: özel örneği deposu oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 593c4e9d-8a49-4e12-8257-cee5e6b4c075
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c383d3af92ba2f76f8ba09bc194220c170beaa0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-custom-instance-store"></a>Nasıl yapılır: özel örneği deposu oluşturma
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]içeren <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, iş akışı verilerinin sürdürülmesi için SQL Server kullanan bir örnek deposu. Uygulamanızı akışı verileri farklı bir veritabanı veya bir dosya sistemi gibi başka bir orta kalıcı hale getirmek için gerekli olduğunda özel örnek deposuna uygulayabilirsiniz. Özel örnek deposuna abstract genişletilerek oluşturulur <xref:System.Runtime.DurableInstancing.InstanceStore> sınıfı ve uygulama için gerekli yöntemleri uygulama. Özel örnek deposuna tam bir uygulama için bkz: [şirket satın alma işlemi](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) örnek.  
  
## <a name="implementing-the-begintrycommand-method"></a>BeginTryCommand yöntemi uygulama  
 <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> Örnek deposuna Kalıcılık altyapısı tarafından gönderilir. Türü `command` parametresi gösterir hangi komutun yürütülen; Bu parametre aşağıdaki türde olabilir:  
  
-   <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: Bir iş akışı depolama ortamına kalıcı olmasını Kalıcılık altyapısı bu komut örnek depoya gönderir. İş akışı Kalıcılık verileri yöntemi için sağlanan <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> üyesi `command` parametresi.  
  
-   <xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: Bir iş akışı depolama ortamından yüklenmesi Kalıcılık altyapısı bu komut örnek deposuna gönderir. Yüklenecek bir iş akışı örneği kimliği yöntemi için sağlanan `instanceId` parametresinin <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> özelliği `context` parametresi.  
  
-   <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>: Bu komut örneğine depolamak Kalıcılık altyapısı gönderir bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> kilit sahibi kayıtlı olması gerekir. Örnek kimliği geçerli bir iş akışı örneğini kullanarak deposu sağlanmalıdır <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> yöntemi `context` parametresi.  
  
     Aşağıdaki kod parçacığını bir açık kilit sahibi atamak için CreateWorkflowOwner komutu uygulamak gösterilmiştir.  
  
    ```  
    XName WFInstanceScopeName = XName.Get(scopeName, "<namespace>");  
    ...  
    CreateWorkflowOwnerCommand createCommand = new CreateWorkflowOwnerCommand()  
    {  
        InstanceOwnerMetadata =  
        {  
            { WorkflowHostTypeName, new InstanceValue(WFInstanceScopeName) },  
        }  
    };  
    InstanceHandle ownerHandle = store.CreateInstanceHandle();  
    store.DefaultInstanceOwner = store.Execute(  
                                   ownerHandle,  
                                   createCommand,  
                                   TimeSpan.FromSeconds(30)).InstanceOwner;  
    childInstance.AddInitialInstanceValues(new Dictionary<XName, object>() { { WorkflowHostTypeName, WFInstanceScopeName } });  
    ```  
  
-   <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: Kilit sahibi örnek kimliği örneği Mağazası'ndan kaldırılabilir Kalıcılık altyapısı örnek deposuna bu komutu gönderir. İle <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, uygulama tarafından kilit sahibi kimliği sağlanmalıdır.  
  
     Aşağıdaki kod parçacığını kullanarak bir kilidi serbest bırakmak gösterilmiştir <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.  
  
    ```  
    static void FreeHandleAndDeleteOwner(InstanceStore store, InstanceHandle handle)  
    {  
        handle.Free();  
        handle = store.CreateInstanceHandle(store.DefaultInstanceOwner);  
        try  
        {  
            // We need this sleep so that we dont prematurely delete the owner, we need time to update the database.  
            Thread.Sleep(10000);  
            store.Execute(handle, new DeleteWorkflowOwnerCommand(), TimeSpan.FromSeconds(10));  
        }  
        catch (InstancePersistenceCommandException ex) { Log.Inform(ex.Message); }  
        catch (InstanceOwnerException ex) { Log.Inform(ex.Message); }  
        catch (OperationCanceledException ex) { Log.Inform(ex.Message); }  
        catch (Exception ex) { Log.Inform(ex.Message); }  
        finally  
        {  
            handle.Free();  
            store.DefaultInstanceOwner = null;  
        }  
    }  
    ```  
  
     Bir alt örneği çalıştırdığınızda, bir Try/Catch bloğu içinde yukarıdaki yöntemi çağrılmalıdır.  
  
    ```  
    try  
    {  
        childInstance.Run();  
    }  
    catch (Exception)  
    {  
        throw ;  
    }  
    finally  
    {  
        FreeHandleAndDeleteOwner(store, ownerHandle);  
    }  
    ```  
  
-   <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: Bir iş akışı örneği iş akışı örneği anahtarı kullanarak yüklenecek Kalıcılık altyapısı bu komut örnek deposuna gönderir. Örnek anahtar Kimliğini kullanarak belirlenebilir <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> komut parametresi.  
  
-   <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: Kalıcılık altyapısı bu komutu, sonra iş yükünü bir iş akışı ana oluşturmak için kalıcı iş akışları için etkinleştirme parametreleri almak için örnek deposuna gönderir. Bu komut örneği deposu oluşturma yanıt altyapısı tarafından gönderilen <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> etkinleştirilebilmesi için bir örnek bulduğunda barındırmak için. Etkinleştirilebilmesi için iş akışları olup olmadığını belirlemek için örnek deposuna sorgulanmak.  
  
-   <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: Kalıcılık altyapısı örnek deposuna runnable iş akışı örnekleri yüklemek için bu komutu gönderir. Bu komut örneği deposu oluşturma yanıt altyapısı tarafından gönderilen <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> çalıştırılabilir bir örneği bulduğunda barındırmak için. Örnek deposuna çalıştırılabilir iş akışları için yoklama. Aşağıdaki kod parçacığını bir örnek deposuna çalıştırmak veya etkin iş akışları için yoklama gösterir.  
  
    ```  
    public void PollForEvents()  
    {  
        InstanceOwner[] storeOwners = this.GetInstanceOwners();  
  
        foreach (InstanceOwner owner in storeOwners)  
        {  
            foreach (InstancePersistenceEvent ppEvent in this.GetEvents(owner))  
            {  
                if (ppEvent.Equals(HasRunnableWorkflowEvent.Value))  
                {  
                    bool hasRunnable = GetRunnableEvents(this.StoreId, owner.InstanceOwnerId, isActivable);  
                    if (hasRunnable)  
                    {  
                        this.SignalEvent(ppEvent, owner);  
                    }  
                    else  
                    {  
                        this.ResetEvent(ppEvent, owner);  
                    }  
                }  
                else if(ppEvent.Equals(HasActivatableWorkflowEvent.Value))  
                {  
                   bool hasActivable = GetActivableEvents(this.StoreId, owner.InstanceOwnerId);  
                   if (hasActivable)  
                    {  
                        this.SignalEvent(ppEvent, owner);  
                    }  
                    else  
                    {  
                        this.ResetEvent(ppEvent, owner);  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
     Yukarıdaki kod parçacığında örnek deposuna kullanılabilir olayları sorgular ve her biri olup olmadığını belirlemek için inceler bir <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> olay. Bulunması durumunda <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> örnek deposuna komut göndermek için ana sinyal için çağrılır.  Aşağıdaki kod parçacığını bir uygulama bu komut için bir işleyici ortaya koyar.  
  
    ```  
    If (command is TryLoadRunnableWorkflowCommand)  
    {  
        Owner owner;  
        CheckOwner(context, command.Name, out owner);                          
        // Checking instance.Owner is like an InstanceLockQueryResult.  
        context.QueriedInstanceStore(new InstanceLockQueryResult(context.InstanceView.InstanceId, context.InstanceView.InstanceOwner.InstanceOwnerId));  
  
        XName ownerService = null;  
        InstanceValue value;  
        Instance runnableInstance = default(Instance);  
        bool foundRunnableInstance = false;  
  
        value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, owner.Data);  
        if (value != null && value.Value is XName)  
        {  
            ownerService = (XName)value.Value;  
        }  
  
        foreach (KeyValuePair<Guid, Instance> instance in MemoryStore.instances)  
        {  
            if (instance.Value.Owner != Guid.Empty || instance.Value.Completed)  
            {  
                continue;  
            }  
  
            if (ownerService != null)  
            {  
                value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, instance.Value.Metadata);  
                if (value == null || ((XName)value.Value) != ownerService)  
                {  
                    continue;  
                }  
            }  
  
            value = QueryPropertyBag(WorkflowServiceNamespace.SuspendReason, instance.Value.Metadata);  
            if (value != null && value.Value != null && value.Value is string)  
            {  
                continue;  
            }  
  
            value = QueryPropertyBag(WorkflowNamespace.Status, instance.Value.Data);  
            if (value != null && value.Value is string && ((string)value.Value) == "Executing")  
            {  
                runnableInstance = instance.Value;  
                foundRunnableInstance = true;  
            }  
  
            if (!foundRunnableInstance)  
            {  
                value = QueryPropertyBag(XNamespace.Get("urn:schemas-microsoft-com:System.Activities/4.0/properties").GetName("TimerExpirationTime"), instance.Value.Data);  
                if (value != null && value.Value is DateTime && ((DateTime)value.Value) <= DateTime.UtcNow)  
                {                          
                    runnableInstance = instance.Value;  
                    foundRunnableInstance = true;  
                }  
            }  
  
            if (foundRunnableInstance)  
            {  
                runnableInstance.LockVersion++;  
                runnableInstance.Owner = context.InstanceView.InstanceOwner.InstanceOwnerId;  
                MemoryStore.instances[instance.Key] = runnableInstance;  
                context.BindInstance(instance.Key);  
                context.BindAcquiredLock(runnableInstance.LockVersion);  
  
                Dictionary<Guid, IDictionary<XName, InstanceValue>> associatedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();  
                Dictionary<Guid, IDictionary<XName, InstanceValue>> completedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();  
                foreach (KeyValuePair<Guid, Key> keyEntry in MemoryStore.keys)  
                {  
                if (keyEntry.Value.Instance == context.InstanceView.InstanceId)  
                {  
                    if (keyEntry.Value.Completed)  
                    {  
                        completedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));  
                    }  
                    else  
                    {  
                        associatedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));  
                    }  
                }  
            }  
  
            context.LoadedInstance(InstanceState.Initialized, DeserializePropertyBag(runnableInstance.Data), DeserializePropertyBag(runnableInstance.Metadata), associatedKeys, completedKeys);  
            break;  
        }  
    }  
    ```  
  
     Yukarıdaki kod parçacığında runnable örnekleri için örnek deposuna arar. Bir örnek bulunursa, yürütme bağlamı bağlı ve yüklendi.  
  
## <a name="using-a-custom-instance-store"></a>Bir özel örnek depolama kullanma  
 Özel örnek deposuna uygulamak için örnek deposuna örneği atamak <xref:System.Activities.WorkflowApplication.InstanceStore%2A>ve uygulamanıza <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> yöntemi.  Bkz: [nasıl yapılır: oluşturun ve uzun çalışan iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) özellikleri için Öğreticisi.  
  
## <a name="a-sample-instance-store"></a>Bir örnek Örnek Depolama  
 Aşağıdaki kod örneği alınan bir tam örnek deposu, uygulamasıdır [şirket satın alma işlemi](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) örnek. Bu örnek deposuna akışı verileri XML kullanarak bir dosyaya devam ettirir.  
  
```  
using System;  
using System.Activities.DurableInstancing;  
using System.Collections.Generic;  
using System.IO;  
using System.Runtime.DurableInstancing;  
using System.Runtime.Serialization;  
using System.ServiceModel.Persistence;  
using System.Xml;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.WF.PurchaseProcess  
{  
  
    public class XmlWorkflowInstanceStore : InstanceStore  
    {  
        Guid ownerInstanceID;  
  
        public XmlWorkflowInstanceStore() : this(Guid.NewGuid())  
        {  
  
        }  
  
        public XmlWorkflowInstanceStore(Guid id)  
        {  
            ownerInstanceID = id;  
        }  
  
        //Synchronous version of the Begin/EndTryCommand functions  
        protected override bool TryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout)  
        {  
            return EndTryCommand(BeginTryCommand(context, command, timeout, null, null));  
        }  
  
        //The persistence engine will send a variety of commands to the configured InstanceStore,  
        //such as CreateWorkflowOwnerCommand, SaveWorkflowCommand, and LoadWorkflowCommand.  
        //This method is where we will handle those commands  
        protected override IAsyncResult BeginTryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout, AsyncCallback callback, object state)  
        {  
            IDictionary<XName, InstanceValue> data = null;  
  
            //The CreateWorkflowOwner command instructs the instance store to create a new instance owner bound to the instanace handle  
            if (command is CreateWorkflowOwnerCommand)  
            {  
                context.BindInstanceOwner(ownerInstanceID, Guid.NewGuid());  
            }  
            //The SaveWorkflow command instructs the instance store to modify the instance bound to the instance handle or an instance key  
            else if (command is SaveWorkflowCommand)  
            {  
                SaveWorkflowCommand saveCommand = (SaveWorkflowCommand)command;  
                data = saveCommand.InstanceData;  
  
                Save(data);  
            }  
            //The LoadWorkflow command instructs the instance store to lock and load the instance bound to the identifier in the instance handle  
            else if (command is LoadWorkflowCommand)  
            {  
                string fileName = IOHelper.GetFileName(this.ownerInstanceID);  
  
                try  
                {  
                    using (FileStream inputStream = new FileStream(fileName, FileMode.Open))  
                    {  
                        data = LoadInstanceDataFromFile(inputStream);  
                        //load the data into the persistence Context  
                        context.LoadedInstance(InstanceState.Initialized, data, null, null, null);  
                    }  
                }  
                catch (Exception exception)  
                {  
                    throw new PersistenceException(exception.Message);  
                }  
            }  
  
            return new CompletedAsyncResult<bool>(true, callback, state);  
        }  
  
        protected override bool EndTryCommand(IAsyncResult result)  
        {  
            return CompletedAsyncResult<bool>.End(result);  
        }  
  
        //Reads data from xml file and creates a dictionary based off of that.  
        IDictionary<XName, InstanceValue> LoadInstanceDataFromFile(Stream inputStream)  
        {  
            IDictionary<XName, InstanceValue> data = new Dictionary<XName, InstanceValue>();  
  
            NetDataContractSerializer s = new NetDataContractSerializer();  
  
            XmlReader rdr = XmlReader.Create(inputStream);  
            XmlDocument doc = new XmlDocument();  
            doc.Load(rdr);  
  
            XmlNodeList instances = doc.GetElementsByTagName("InstanceValue");  
            foreach (XmlElement instanceElement in instances)  
            {  
                XmlElement keyElement = (XmlElement)instanceElement.SelectSingleNode("descendant::key");  
                XName key = (XName)DeserializeObject(s, keyElement);  
  
                XmlElement valueElement = (XmlElement)instanceElement.SelectSingleNode("descendant::value");  
                object value = DeserializeObject(s, valueElement);  
                InstanceValue instVal = new InstanceValue(value);  
  
                data.Add(key, instVal);  
            }  
  
            return data;  
        }  
  
        object DeserializeObject(NetDataContractSerializer serializer, XmlElement element)  
        {  
            object deserializedObject = null;  
  
            MemoryStream stm = new MemoryStream();  
            XmlDictionaryWriter wtr = XmlDictionaryWriter.CreateTextWriter(stm);  
            element.WriteContentTo(wtr);  
            wtr.Flush();  
            stm.Position = 0;  
  
            deserializedObject = serializer.Deserialize(stm);  
  
            return deserializedObject;  
        }  
  
        //Saves the persistence data to an xml file.  
        void Save(IDictionary<XName, InstanceValue> instanceData)  
        {  
            string fileName = IOHelper.GetFileName(this.ownerInstanceID);  
            XmlDocument doc = new XmlDocument();  
            doc.LoadXml("<InstanceValues/>");  
  
            foreach (KeyValuePair<XName,InstanceValue> valPair in instanceData)  
            {  
                XmlElement newInstance = doc.CreateElement("InstanceValue");  
  
                XmlElement newKey = SerializeObject("key", valPair.Key, doc);  
                newInstance.AppendChild(newKey);  
  
                XmlElement newValue = SerializeObject("value", valPair.Value.Value, doc);  
                newInstance.AppendChild(newValue);  
  
                doc.DocumentElement.AppendChild(newInstance);  
            }  
            doc.Save(fileName);  
       }  
  
        XmlElement SerializeObject(string elementName, object o, XmlDocument doc)  
        {  
            NetDataContractSerializer s = new NetDataContractSerializer();  
            XmlElement newElement = doc.CreateElement(elementName);  
            MemoryStream stm = new MemoryStream();  
  
            s.Serialize(stm, o);  
            stm.Position = 0;  
            StreamReader rdr = new StreamReader(stm);  
            newElement.InnerXml = rdr.ReadToEnd();  
  
            return newElement;  
        }  
    }  
}  
```
